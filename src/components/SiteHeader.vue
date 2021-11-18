<template>
  <header class="d-flex align-items-center justify-content-between">
    <div class="site_logo">
      <h1>BOOLFLIX</h1>
    </div>
    <search-bar />
  </header>
</template>

<script>
import SearchBar from "./SearchBar.vue";
export default {
  components: { SearchBar },
};
</script>

<style lang="scss">
header {
  height: 100px;
  background-color: rgb(22, 22, 22);
  h1 {
    color: red;
    line-height: 100px;
    padding-left: 2rem;
  }
}
</style>