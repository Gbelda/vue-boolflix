<template>
  <div class="col-12 col-md-6 col-lg-4 col-xl-3 col-xxl-2 show">
    <div class="poster">
      <img :src="this.getPoster" alt="" class="poster_img" />
      <div class="show_data col-12">
        <h2>{{ title }}</h2>
        <h4>{{ original_title }}</h4>
        <h4>
          <img
            :src="require(`../assets/flags/${transformLanguage}.svg`)"
            class="flag"
          />
          {{ language }}
        </h4>
        <h4>Rating:</h4>
        <star-rating
          class="star"
          :star-size="20"
          :read-only="true"
          :rating="this.transformVote"
          :show-rating="false"
        />
        <cast-list :showId="showId" />
      </div>
    </div>
  </div>
</template>

<script>
import StarRating from "../../node_modules/vue-star-rating/src/star-rating.vue";
import CastList from "./CastList.vue";
export default {
  components: {
    StarRating,
    CastList,
  },
  data() {
    return {
      isSelected: false,
    };
  },
  props: {
    showId: Number,
    title: String,
    original_title: String,
    language: String,
    vote_avg: Number,
    langArray: Array,
    imgURL: String,
  },
  computed: {
    transformLanguage() {
      if (!this.langArray.includes(this.language)) {
        return "xx";
      } else {
        return this.language;
      }
    },
    transformVote() {
      return Math.ceil(this.vote_avg / 2);
    },
    getPoster() {
      return this.imgURL == null
        ? require("../assets/question.jpg")
        : `https://image.tmdb.org/t/p/w342//${this.imgURL}`;
    },
  },
  methods: {
    clearList() {
      this.isSelected = false;
    },
  },
};
</script>

<style lang="scss">
</style>