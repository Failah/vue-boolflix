<template>
  <div class="main-container">
    <MoviesListComponent :movies="movies" />
    <SeriesListComponent :series="series" />
  </div>
</template>

<script>
import MoviesListComponent from "@/components/MoviesListComponent.vue";
import SeriesListComponent from "@/components/SeriesListComponent.vue";

export default {
  name: "MainComponent",

  components: {
    MoviesListComponent,
    SeriesListComponent,
  },

  props: {
    movies: Array,
    series: Array,
  },
};
</script>

<style lang="scss" scoped>
.main-container {
  background-color: #141414;
  color: white;
  min-height: 92vh;
}
</style>