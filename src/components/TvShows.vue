<template>
  <div class="col-3 tv_show">
    <div class="show_data">
      <h2>{{ name }}</h2>
      <h4>{{ original_name }}</h4>
      <h4>
        <img
          :src="require(`../assets/flags/${transformLanguage}.svg`)"
          class="flag"
        />
        {{ language }}
      </h4>
      <h4>vote average : {{ this.transformVote }}</h4>
    </div>
    <div class="poster">
      <img :src="`https://image.tmdb.org/t/p/w342//${this.imgURL}`" alt="" />
    </div>
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
    langArray: Array,
    imgURL: String,
  },
  computed: {
    transformLanguage() {
      if (!this.langArray.includes(this.language)) {
        return "xx";
      } else {
        return this.language;
      }
    },
    transformVote() {
      return Math.ceil(this.vote_avg / 2);
    },
  },
};
</script>

<style lang="scss">
.tv_show {
  padding: 2rem 0px;
  text-align: center;
  .show_data {
    max-width: 342px;
    margin: auto;
  }
}
</style>