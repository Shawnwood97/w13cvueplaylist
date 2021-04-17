<template>
  <main>
    <play-list />
    <song-list />
  </main>
</template>

<script>
import PlayList from "./PlayList.vue";
import SongList from "./SongList.vue";
export default {
  components: { PlayList, SongList },
  name: "page-body",
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
</style>
