<template>
  <div class="col-3 tv_show">
    <h2>{{ name }}</h2>
    <h4>{{ original_name }}</h4>
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
    name: String,
    original_name: String,
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
.tv_show {
  padding: 2rem 0px;
}
</style>