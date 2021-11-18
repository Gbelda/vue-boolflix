<template>
  <div id="app">
    <site-header />
    <site-main />
  </div>
</template>

<script>
import SiteHeader from "./components/SiteHeader.vue";
import SiteMain from "./components/SiteMain.vue";

export default {
  name: "App",
  components: {
    SiteHeader,
    SiteMain,
  },
};
</script>

<style lang="scss">
@import "./assets/scss/common.scss";
@import "../node_modules/bootstrap/scss/bootstrap.scss";
</style>
