<template>
  <div class="col-3 movie">
    <h2>{{ title }}</h2>
    <h4>{{ original_title }}</h4>
    <h4>
      <img
        :src="require(`../assets/flags/${transformLanguage}.svg`)"
        class="flag"
      />
      {{ language }}
    </h4>
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
    langArray: Array,
  },
  computed: {
    transformLanguage() {
      if (!this.langArray.includes(this.language)) {
        return "xx";
      } else {
        return this.language;
      }
    },
  },
};
</script>

<style lang="scss">
.movie {
  padding: 2rem 0px;
}
</style>