<template>
  <div class="col-3 movie">
    <h1>{{ title }}</h1>
    <h4>{{ original_title }}</h4>
    <h4>{{ language }}</h4>
    <h4>vote average : {{ vote_avg }}</h4>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    original_title: String,
    language: String,
    vote_avg: Number,
  },
};
</script>

<style>
</style>