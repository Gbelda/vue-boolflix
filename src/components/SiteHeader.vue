<template>
  <header class="d-flex align-items-center justify-content-between">
    <div class="site_logo">
      <h1>BOOLFLIX</h1>
    </div>
    <div class="search_el">
      <input
        type="text"
        name="search"
        id="search_input"
        placeholder="Search a Title"
        v-model="searchString"
        @keyup.enter="$emit('search', searchString)"
      />
      <button @click="$emit('submit-search', searchString)">Search</button>
    </div>
  </header>
</template>

<script>
export default {
  components: {},
  props: {
    searchText: String,
  },
  data() {
    return {
      searchString: "",
    };
  },
};
</script>

<style lang="scss">
header {
  position: fixed;
  width: 100%;
  height: 100px;
  background-color: rgb(22, 22, 22);
  z-index: 99;
  h1 {
    color: red;
    line-height: 100px;
    padding-left: 2rem;
  }
  .search_el {
    padding-right: 2rem;
    button {
      padding: 1px 10px;
      border: none;
    }
  }
}
</style>