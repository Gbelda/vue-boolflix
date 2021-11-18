<template>
  <div id="app">
    <site-header />
  </div>
</template>

<script>
import SiteHeader from "./components/SiteHeader.vue";

export default {
  name: "App",
  components: {
    SiteHeader,
  },
};
</script>

<style lang="scss">
@import "./assets/scss/common.scss";
@import "../node_modules/bootstrap/scss/bootstrap.scss";
</style>
