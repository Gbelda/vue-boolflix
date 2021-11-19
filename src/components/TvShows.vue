<template>
  <div class="col-3 tv_show">
    <h2>{{ name }}</h2>
    <h4>{{ original_name }}</h4>
    <h4>
      <img :src="require(`../assets/flags/${language}.svg`)" class="flag" />
      {{ language }}
    </h4>
    <h4>vote average : {{ vote_avg }}</h4>
  </div>
</template>

<script>
export default {
  data() {
    return {
      filterLanguage: this.langArray,
    };
  },
  props: {
    name: String,
    original_name: String,
    language: String,
    vote_avg: Number,
    langArray: Array,
  },
};
</script>

<style lang="scss">
.tv_show {
  padding: 2rem 0px;
}
</style>