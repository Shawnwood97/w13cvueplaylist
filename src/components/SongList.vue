<template>
  <!-- onclick run notifyParent function with argument of item passed through as a prop -->

  <div class="listContainer">
    <h2 class="listContainerHeader">Your Song List</h2>
    <!-- conditional to display a message when array has content. aka true.-->
    <div v-if="songs[0]">
      <!-- Display each song item, goes inside the array and for each object within the array passes variable song into the 
      function when we the corrosponding div, then, in the function declaration below it sends the information to the parent (PageBody) to be
      used in another function there! -->
      <div
        class="songItem"
        v-for="song in songs"
        :key="song.id"
        @click="notifyParent(song)"
      >
        <!-- displays the info from the key value pairs in the array objects using MOOOOOstache syntax -->
        <h4>{{ song.name }}</h4>
        <h5>{{ song.artist }}</h5>
      </div>
    </div>

    <!-- What to display when conditional fails -->
    <div class="noItemsCont" v-else>
      <h2>No Items In Song List</h2>
      <p>You can move items from your Play List by clicking on them</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "song-list",
  // expect prop songs to be an array, which is the full(because no storage will always be the default full array) array of songs from PageBody
  props: {
    songs: Array,
  },

  methods: {
    // emit songs back to the parent, to be called by using @toPlayList = "function" which exists in parent
    notifyParent(data) {
      this.$emit("toPlayList", data);
    },
  },
};
</script>

<style lang="scss" scoped>
.songItem {
  display: grid;
  place-items: center;
  background: #393e46;
  border: 1px solid #14181d;
  margin: 5px;
  user-select: none;
  &:hover {
    cursor: pointer;
  }
}

.listContainer {
  background: #222831;
  height: 500px;
  width: 100%;
  overflow-y: auto;
  border-radius: 10px;
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

.noItemsCont {
  display: grid;
  place-items: center;
  height: 100px;
}
</style>
