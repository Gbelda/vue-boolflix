<template>
  <main>
    <div class="container">
      <div class="row" v-if="!noMovie">
        <movie
          v-for="movie in movies"
          :key="movie.id"
          :title="movie.title"
          :original_title="movie.original_title"
          :language="movie.original_language"
          :vote_avg="movie.vote_average"
        />
      </div>
      <div class="no_movie" v-else>
        <h1>{{ error }}</h1>
      </div>
    </div>
  </main>
</template>

<script>
import Movie from "./Movie.vue";
export default {
  props: {
    movies: Array,
    error: String,
    noMovie: Boolean,
  },
  components: {
    Movie,
  },
  data() {
    return {};
  },
};
</script>

<style lang="scss">
.no_movie {
  h1 {
    padding-top: 10rem;
    color: red;
    text-align: center;
  }
}
</style>