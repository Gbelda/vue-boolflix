<template>
  <div class="col-12 col-md-6 col-lg-4 col-xl-3 col-xxl-2 show">
    <div class="poster">
      <img
        :src="`https://image.tmdb.org/t/p/w342//${this.imgURL}`"
        alt=""
        class="poster_img"
      />
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
      </div>
    </div>
  </div>
</template>

<script>
import StarRating from "../../node_modules/vue-star-rating/src/star-rating.vue";
export default {
  components: {
    StarRating,
  },
  data() {
    return {};
  },
  props: {
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
  },
};
</script>

<style lang="scss">
</style>