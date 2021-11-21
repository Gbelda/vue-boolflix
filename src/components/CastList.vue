<template>
  <div class="cast_list">
    <h6 class="api_link" @click="generateCastList()">See casts..</h6>
    <ul class="casts">
      <li v-for="cast in castList" :key="cast.id">
        {{ cast.name }} as {{ cast.character }}
      </li>
    </ul>
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
    };
  },
  props: {
    showId: Number,
    clearList: [],
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
  },
  mounted() {
    axios
      .get(
        `https://api.themoviedb.org/3/movie/${this.showId}/credits?api_key=a0f48b175c1403d06b6b5b6c03c79b28&language=it`
      )
      .then((response) => {
        this.allCast = response.data.cast;
      });
  },
};
</script>

<style  lang='scss'>
.casts {
  padding: 0;
}
</style>