<template>
  <div class="movies-container">
    <h2>Lista dei Film:</h2>
    <div class="card" v-for="movie in movies" :key="movie.id">
      <div><span>Titolo: </span>{{ movie.title }}</div>
      <p><span>Titolo Originale: </span>{{ movie.original_title }}</p>
      <p><span>Valutazione: </span>{{ movie.vote_average }}</p>
      <p>
        <span>Lingua: </span>
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
        case "ko": {
          country = "xk";
          break;
        }
        case "hi": {
          country = "in";
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
.movies-container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  // justify-content: space-between;
  column-gap: 20px;

  h2 {
    width: 100%;
    margin: 20px 0px;
    text-decoration: underline;
  }

  .card {
    border: 1px solid grey;
    width: calc(100% / 3 - 20px);
    margin-bottom: 20px;

    p {
      margin-top: 5px;
    }
  }
}

.lang-flag {
  width: 20px;
}
</style>