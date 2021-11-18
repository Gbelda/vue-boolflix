<template>
  <div id="app">
    <site-header />
    <site-main :movies="this.movies" />
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
      titleString: "",
      query: "star",
      movies: [],
    };
  },
  components: {
    SiteHeader,
    SiteMain,
  },
  mounted() {
    axios
      .get(
        `https://api.themoviedb.org/3/search/movie?api_key=a0f48b175c1403d06b6b5b6c03c79b28&language=it&include_adult=false&query=${this.query}`
      )
      .then((response) => {
        this.movies = response.data.results;
      })
      .catch((error) => {
        alert(error);
      });
  },
};
</script>

<style lang="scss">
@import "./assets/scss/common.scss";
@import "../node_modules/bootstrap/scss/bootstrap.scss";
</style>
