<template>
  <div id="app">
    <page-header />
    <page-body />
    <page-footer />
  </div>
</template>

<script>
import PageBody from "./components/PageBody.vue";
import PageFooter from "./components/PageFooter.vue";
import PageHeader from "./components/PageHeader.vue";
export default {
  name: "App",
  components: { PageHeader, PageBody, PageFooter },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
