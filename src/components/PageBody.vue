<template>
  <main>
    <!-- just a container for styling -->
    <div id="container">
      <!-- gets item from emit in playList.vue and uses function below to update arrays, displays the SongList component. -->
      <!-- sends prop songs as an object to songList.vue with KVP's from songObject -->
      <song-list @toPlayList="getObjectFromSongList" :songs="songObject" />

      <!-- gets item from emit in playList.vue and uses function below to update objects, displays items from clickedSongs object if it passes conditional -->
      <!-- sends prop songs as an object to playList.vue with KVP's from clickedSongs-->
      <play-list @toSongList="getObjectFromPlayList" :songs="clickedSongs" />
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
    // function to remove object from songObject and add to clickedSongs
    getObjectFromSongList(data) {
      this.clickedSongs.push(data);
      this.songObject.splice(this.songObject.indexOf(data), 1);
    },
    // function to remove object from clickedSongs and add to songObject
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
</style>
