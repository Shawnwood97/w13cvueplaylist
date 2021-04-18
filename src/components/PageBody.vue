<template>
  <main>
    <div id="songListContainer">
      <div v-if="this.songObject[0]">
        <song-list
          @toPlayList="getObjectFromSongList"
          v-for="song in this.songObject"
          :key="song.id"
          :songs="song"
        />
      </div>

      <h4 v-else>No Items In Song List</h4>
    </div>

    <div id="playListContainer">
      <div v-if="this.clickedSongs[0]">
        <play-list
          @toSongList="getObjectFromPlayList"
          v-for="song in this.clickedSongs"
          :key="song.id"
          :clickedSongs="song"
        />
      </div>
      <h4 v-else>No Songs In Playlist</h4>
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
    getObjectFromSongList(data) {
      this.clickedSongs.push(data);
      this.songObject.splice(this.songObject.indexOf(data), 1);
      console.log(this.songObject);
    },

    getObjectFromPlayList(data) {
      this.songObject.push(data);
      this.clickedSongs.splice(this.clickedSongs.indexOf(data), 1);
    },
  },

  data() {
    return {
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
  grid-auto-flow: column;
  place-items: center;
  height: 92vh;
  background: rgb(192, 176, 155);
}

#songListContainer {
  background: red;
  height: 500px;
  width: 500px;
}

#playListContainer {
  background: blue;
  height: 500px;
  width: 500px;
}
</style>
