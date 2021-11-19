<template>
  <div id="app">
    <site-header @search="getShows" @submit-search="getShows" />
    <site-main
      :shows="this.shows"
      :movies="this.movies"
      :error="this.error"
      :noMovie="this.noMovie"
      :languagesArray="this.languages"
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
      allResults: [],
      query: "A",
      movies: [],
      shows: [],
      languages: [],
      error: "",
      noMovie: false,
      moviesURI:
        "https://api.themoviedb.org/3/search/movie?api_key=a0f48b175c1403d06b6b5b6c03c79b28&language=it&include_adult=false&query=",
      showsURI:
        "https://api.themoviedb.org/3/search/tv?api_key=a0f48b175c1403d06b6b5b6c03c79b28&language=it&include_adult=false&query=",
    };
  },
  components: {
    SiteHeader,
    SiteMain,
  },
  methods: {
    callShowsAPI(text) {
      let callMovie = axios.get(this.moviesURI + text);
      let callShows = axios.get(this.showsURI + text);
      axios
        .all([callMovie, callShows])
        .then(
          axios.spread((...responses) => {
            this.movies = responses[0].data.results;
            this.shows = responses[1].data.results;
            this.allResults = [...this.movies, ...this.shows];
            this.getLanguage(this.allResults);
          })
        )

        .catch((errors) => {
          alert(errors);
        });
    },
    getShows(text) {
      if (text.length > 0) {
        this.language = [];
        this.callShowsAPI(text);
        this.noMovie = false;
      } else {
        this.shows = [];
        this.movies = [];
        this.error = "Search a Movie Title or Tv show";
        this.noMovie = true;
      }
    },
    getLanguage(array) {
      let filterLanguages = [];
      for (let index = 0; index < array.length; index++) {
        if (!filterLanguages.includes(array[index].original_language))
          filterLanguages.push(array[index].original_language);
      }
      this.languages = filterLanguages;
    },
  },
  mounted() {
    this.callShowsAPI(this.query);
  },
};
</script>

<style lang="scss">
@import "./assets/scss/common.scss";
@import "../node_modules/bootstrap/scss/bootstrap.scss";
</style>
