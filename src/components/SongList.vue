<template>
  <div @click="notifyParent(songs)" class="indSongContainer">
    <h4>{{ songs.name }}</h4>
    <h5>{{ songs.artist }}</h5>
  </div>
</template>

<script>
export default {
  name: "song-list",
  props: {
    songs: Object,
  },

  methods: {
    notifyParent(songs) {
      this.$emit("toPlayList", songs);
    },
  },
};
</script>

<style lang="scss" scoped>
div {
  display: grid;
  place-items: center;
  background: white;
  border: 1px solid black;
  margin: 5px;
  &:hover {
    cursor: pointer;
  }
}
</style>
