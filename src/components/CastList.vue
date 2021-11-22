<template>
  <div class="cast_list">
    <h6 class="api_link" @click="generateCastList()">See casts..</h6>
    <ul class="casts" v-if="allCast != []">
      <li v-for="cast in castList" :key="cast.id">
        {{ cast.name }} as {{ cast.character }}
      </li>
    </ul>
    <h6 v-else>There is no cast list...</h6>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      castList: [],
      allCast: [],
      isShowing: false,
      castURI: "",
    };
  },
  props: {
    showId: Number,
    isMovie: Boolean,
  },
  methods: {
    generateCastList() {
      if (this.isShowing == false) {
        for (let index = 0; index < 5; index++) {
          if (!this.castList.includes(this.allCast[index])) {
            this.castList.push(this.allCast[index]);
          }
        }
        this.isShowing = true;
      } else {
        this.castList = [];
        this.isShowing = false;
      }
    },
    isCastKnown() {},
  },
  mounted() {
    axios.get(this.getCast).then((response) => {
      this.allCast = response.data.cast;
    });
  },
  computed: {
    getCast() {
      return this.isMovie == true
        ? `https://api.themoviedb.org/3/movie/${this.showId}/credits?api_key=a0f48b175c1403d06b6b5b6c03c79b28`
        : `https://api.themoviedb.org/3/tv/${this.showId}/credits?api_key=a0f48b175c1403d06b6b5b6c03c79b28`;
    },
  },
};
</script>

<style  lang='scss'>
.casts {
  padding: 0;
}
</style>