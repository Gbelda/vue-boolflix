<template>
  <main>
    <div class="container-fluid">
      <div class="row" v-if="!noMovie">
        <h1 class="section">MOVIES</h1>
        <movie
          v-for="movie in movies"
          :key="movie.id"
          :title="movie.title"
          :original_title="movie.original_title"
          :language="movie.original_language"
          :vote_avg="movie.vote_average"
          :imgURL="movie.poster_path"
          :langArray="languagesArray"
          :movieId="movie.id"
        />
        <h1 class="section">TV SHOWS</h1>
        <tv-shows
          v-for="show in shows"
          :key="show.id"
          :name="show.name"
          :original_name="show.original_name"
          :language="show.original_language"
          :vote_avg="show.vote_average"
          :imgURL="show.poster_path"
          :langArray="languagesArray"
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
import TvShows from "./TvShows.vue";
export default {
  props: {
    shows: Array,
    movies: Array,
    error: String,
    noMovie: Boolean,
    languagesArray: Array,
  },
  components: {
    Movie,
    TvShows,
  },
  data() {
    return {};
  },
};
</script>

<style lang="scss">
main {
  min-height: 100vh;
  background-color: rgb(44, 44, 44);
  padding-top: 50px;
  .section {
    padding-top: 5rem;
    color: white;
    font-size: 3rem;
  }
  .no_movie {
    h1 {
      padding-top: 10rem;
      color: red;
      text-align: center;
    }
  }
}
</style>