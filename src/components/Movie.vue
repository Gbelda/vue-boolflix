<template>
  <div class="col-3 movie">
    <h1>{{ title }}</h1>
    <h4>{{ original_title }}</h4>
    <h4>{{ getFlagEmoji(language) }}</h4>
    <h4>vote average : {{ vote_avg }}</h4>
  </div>
</template>

<script>
export default {
  data() {
    return {
      code: this.language,
    };
  },
  props: {
    title: String,
    original_title: String,
    language: String,
    vote_avg: Number,
  },
  methods: {
    getFlagEmoji(countryCode) {
      const codePoints = countryCode
        .toUpperCase()
        .split("")
        .map((char) => 127397 + char.charCodeAt());
      return String.fromCodePoint(...codePoints);
    },
  },
};
</script>

<style lang="scss">
.movie {
  padding-top: 2rem;
}
</style>