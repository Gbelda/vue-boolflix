<template>
  <div id="app">
    <site-header @search="getShows" />
    <site-main
      :shows="this.shows"
      :movies="this.movies"
      :error="this.error"
      :noMovie="this.noMovie"
    />
  </div>
</template>

<script>
import SiteHeader from "./components/SiteHeader.vue";
import SiteMain from "./components/SiteMain.vue";
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      query: "A",
      shows: [],
      movies: [],
      error: "",
      noMovie: false,
    };
  },
  components: {
    SiteHeader,
    SiteMain,
  },
  methods: {
    callMoviesAPI(text) {
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie?api_key=a0f48b175c1403d06b6b5b6c03c79b28&language=it&include_adult=false&query=" +
            text
        )
        .then((response) => {
          this.movies = response.data.results;
        })
        .catch((error) => {
          alert(error);
        });
    },
    callTvShowsAPI(text) {
      axios
        .get(
          "https://api.themoviedb.org/3/search/tv?api_key=a0f48b175c1403d06b6b5b6c03c79b28&language=it&include_adult=false&query=" +
            text
        )
        .then((response) => {
          this.shows = response.data.results;
        })
        .catch((error) => {
          alert(error);
        });
    },
    getShows(text) {
      if (text.length > 0) {
        this.callMoviesAPI(text);
        this.callTvShowsAPI(text);
        this.noMovie = false;
      } else {
        this.shows = [];
        this.movies = [];
        this.error = "Search a Movie Title or Tv show";
        this.noMovie = true;
      }
    },
  },
  mounted() {
    this.callMoviesAPI(this.query);
    this.callTvShowsAPI(this.query);
  },
};
</script>

<style lang="scss">
@import "./assets/scss/common.scss";
@import "../node_modules/bootstrap/scss/bootstrap.scss";
</style>
