<template>
  <!-- onclick run notifyParent function with argument of item passed through as a prop -->
  <div @click="notifyParent(songs)">
    <h4>{{ songs.name }}</h4>
    <h5>{{ songs.artist }}</h5>
  </div>
</template>

<script>
export default {
  name: "play-list",
  // expect prop songs to be an object
  props: {
    songs: Object,
  },

  methods: {
    // emit songs back to the parent, to be called by using @toSongList = "function" which exists in parent
    notifyParent(songs) {
      this.$emit("toSongList", songs);
    },
  },
};
</script>

<style lang="scss" scoped>
div {
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
</style>
