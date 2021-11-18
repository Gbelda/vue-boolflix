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
import axios from "axios";
import Movie from "./Movie.vue";
export default {
  components: {
    Movie,
  },
  data() {
    return {
      query: "star",
      movies: [],
    };
  },
  mounted() {
    axios
      .get(
        `https://api.themoviedb.org/3/search/movie?api_key=a0f48b175c1403d06b6b5b6c03c79b28&language=it&include_adult=false&query=${this.query}`
      )
      .then((response) => {
        this.movies = response.data.results;
        this.loading = false;
      })
      .catch((error) => {
        alert(error);
      });
  },
};
</script>

<style lang="scss">
.movie {
  padding-top: 2rem;
}
</style>