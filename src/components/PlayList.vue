<template>
  <div @click="notifyParent(clickedSongs)">
    <h4>{{ clickedSongs.name }}</h4>
    <h5>{{ clickedSongs.artist }}</h5>
  </div>
</template>

<script>
export default {
  name: "play-list",
  props: {
    clickedSongs: Object,
  },

  methods: {
    notifyParent(clickedSongs) {
      this.$emit("toSongList", clickedSongs);
    },
  },
};
</script>

<style lang="scss" scoped>
div {
  display: grid;
  place-items: center;
  background: white;
  // border: 1px solid black;
  margin: 5px;

  &:hover {
    cursor: pointer;
  }
}
</style>
