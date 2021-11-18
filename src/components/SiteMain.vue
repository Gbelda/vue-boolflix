<template>
  <main>
    <div class="container">
      <div class="row">
        <movie
          v-for="movie in movies"
          :key="movie.id"
          :title="movie.title"
          :original_title="movie.original_title"
          :language="movie.original_language"
          :vote_avg="movie.vote_average"
        />
      </div>
    </div>
  </main>
</template>

<script>
import Movie from "./Movie.vue";
export default {
  props: {
    movies: Array,
  },
  components: {
    Movie,
  },
  data() {
    return {
      query: "star",
    };
  },
};
</script>

<style lang="scss">
.movie {
  padding-top: 2rem;
}
</style>