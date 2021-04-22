<template>
  <!-- This functions identically to SongList with 1 change, the passed array instead of being the default array full of items will be the clickedSongs array 
which is declared as empty in PageBody and gets filled using emit from SongList > PageBody > PlayList -->

  <!-- onclick run notifyParent function with argument of item passed through as a prop -->
  <div class="listContainer">
    <div class="listContainerHeader"><h2>Your Play List</h2></div>

    <div v-if="songs[0]">
      <div
        class="songItem"
        v-for="song in songs"
        :key="song.id"
        @click="notifyParent(song)"
      >
        <h4>{{ song.name }}</h4>
        <h5>{{ song.artist }}</h5>
      </div>
    </div>

    <div class="noItemsCont" v-else>
      <h2>No Items In Play List</h2>
      <p>You can move items from your Song List by clicking on them</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "play-list",

  props: {
    songs: Array,
  },

  methods: {
    // emit songs back to the parent, to be called by using @toSongList = "function" which exists in parent
    notifyParent(data) {
      this.$emit("toSongList", data);
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
