<template>
  <main>
    <div id="container">
      <div class="listContainer">
        <div class="listContainerHeader"><h2>Your Song List</h2></div>
        <!-- conditional to display a message when item at position 0 in object is empty -->
        <div v-if="this.songObject[0]">
          <!-- gets item from emit in playList.vue and uses function below to update objects, displays items from songObject object if it passes conditional -->
          <!-- sends prop songs as an object to songList.vue with KVP's from songObject -->
          <song-list
            @toPlayList="getObjectFromSongList"
            v-for="song in this.songObject"
            :key="song.id"
            :songs="song"
          />
        </div>

        <div class="noItemsCont" v-else>
          <h2>No Items In Song List</h2>
          <p>You can move items ftom your Play List by clicking on them</p>
        </div>
      </div>

      <div class="listContainer">
        <div class="listContainerHeader"><h2>Your Play List</h2></div>
        <!-- conditional to display a message when item at position 0 in object is empty -->
        <div v-if="this.clickedSongs[0]">
          <!-- gets item from emit in playList.vue and uses function below to update objects, displays items from clickedSongs object if it passes conditional -->
          <!-- sends prop songs as an object to playList.vue with KVP's from clickedSongs-->
          <play-list
            @toSongList="getObjectFromPlayList"
            v-for="song in this.clickedSongs"
            :key="song.id"
            :songs="song"
          />
        </div>
        <div class="noItemsCont" v-else>
          <h2>No Items In Play List</h2>
          <p>You can move items ftom your Song List by clicking on them</p>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import PlayList from "./PlayList.vue";
import SongList from "./SongList.vue";
export default {
  components: { PlayList, SongList },
  name: "page-body",

  methods: {
    // function to remove item from songObject and add to clickedSongs
    getObjectFromSongList(data) {
      this.clickedSongs.push(data);
      this.songObject.splice(this.songObject.indexOf(data), 1);
    },
    // function to remove item from clickedSongs and add to songObject
    getObjectFromPlayList(data) {
      this.songObject.push(data);
      this.clickedSongs.splice(this.clickedSongs.indexOf(data), 1);
    },
  },

  data() {
    return {
      // declare empty array for storing our clicked items as an object.
      clickedSongs: [],
      songObject: [
        {
          name: "Smells Like Teen Spirit",
          artist: "Nirvana",
          id: 1,
        },
        {
          name: "Imagine",
          artist: "John Lennon",
          id: 2,
        },
        {
          name: "One",
          artist: "U2",
          id: 3,
        },
        {
          name: "Billie Jean",
          artist: "Michael Jackson",
          id: 4,
        },
        {
          name: "Bohemian Rhapsody",
          artist: "Queen",
          id: 5,
        },
        {
          name: "Hey Jude",
          artist: "The Beatles",
          id: 6,
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
main {
  display: grid;
  place-items: center;
  min-height: 92vh;
  background: #393e46;
  padding: 20px;
  width: 100%;
}

#container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
  gap: 20px;
  width: 70%;
}

.listContainerHeader {
  background: #00adb5;
  border-radius: 10px 10px 0 0;
  color: #222831;
  font-weight: bold;
  display: grid;
  place-items: center;
  height: 40px;
}

.listContainer {
  background: #222831;
  height: 500px;
  width: 100%;
  overflow-y: auto;
  border-radius: 10px;
}

.noItemsCont {
  display: grid;
  place-items: center;
  height: 100px;
}
</style>
