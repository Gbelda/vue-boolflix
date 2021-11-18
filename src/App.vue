<template>
  <div id="app">
    <site-header @search="getMovies" />
    <site-main
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
    callAPI(text) {
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
    getMovies(text) {
      if (text.length > 0) {
        this.callAPI(text);
        this.noMovie = false;
      } else {
        this.movies = [];
        this.error = "Search a movie Title";
        this.noMovie = true;
      }
    },
  },
  mounted() {
    this.callAPI(this.query);
  },
};
</script>

<style lang="scss">
@import "./assets/scss/common.scss";
@import "../node_modules/bootstrap/scss/bootstrap.scss";
</style>
