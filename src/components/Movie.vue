<template>
  <div class="col-3 movie">
    <h2>{{ title }}</h2>
    <h4>{{ original_title }}</h4>

    <img :src="require(`../assets/flags/${language}.svg`)" />
    <h4>vote average : {{ vote_avg }}</h4>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: {
    title: String,
    original_title: String,
    language: String,
    vote_avg: Number,
  },
};
</script>

<style lang="scss">
.movie {
  padding: 2rem 0px;
}
</style>