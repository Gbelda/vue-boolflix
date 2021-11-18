<template>
  <div class="col-3 tv_show">
    <h2>{{ name }}</h2>
    <h4>{{ original_name }}</h4>
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
    name: String,
    original_name: String,
    language: String,
    vote_avg: Number,
  },
};
</script>

<style lang="scss">
.tv_show {
  padding: 2rem 0px;
}
</style>