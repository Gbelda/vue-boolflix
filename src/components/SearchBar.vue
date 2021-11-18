<template>
  <div class="search_el">
    <input
      type="text"
      name="search"
      id="search_input"
      placeholder="Movie Title"
      v-model="titleString"
      @keyup.enter="$emit('search', titleString)"
    />
    <button>Search</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titleString: "",
    };
  },
};
</script>

<style lang="scss">
.search_el {
  padding-right: 2rem;
}
</style>