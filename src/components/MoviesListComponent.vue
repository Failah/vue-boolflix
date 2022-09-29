<template>
  <div>
    <div v-for="movie in movies" :key="movie.id">
      <div>{{ movie.title }}</div>
      <p>{{ movie.original_title }}</p>
      <p>{{ movie.vote_average }}</p>
      <p>
        <img
          class="lang-flag"
          :src="getFlag(movie.original_language)"
          :alt="movie.original_language"
          @error="fixImgError($event)"
        />
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "MoviesListComponent",

  props: {
    movies: Array,
  },

  methods: {
    getFlag(country) {
      switch (country) {
        case "en": {
          country = "gb";
          break;
        }
        case "ja": {
          country = "jp";
          break;
        }
        case "da": {
          country = "dk";
          break;
        }
      }
      return `https://flagicons.lipis.dev/flags/1x1/${country}.svg`;
    },

    fixImgError(event) {
      event.target.src = `https://flagicons.lipis.dev/flags/1x1/xx.svg`;
    },
  },
};
</script>

<style lang="scss" scoped>
.lang-flag {
  width: 20px;
}
</style>