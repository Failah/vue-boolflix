<template>
  <div class="series-container">
    <h2>Lista delle serie TV:</h2>
    <div class="card" v-for="serie in series" :key="serie.id">
      <div>
        <img
          :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path"
          alt=""
          @error="fixThumbError($event)"
        />
      </div>
      <div><span>Titolo: </span>{{ serie.name }}</div>
      <p><span>Titolo Originale: </span>{{ serie.original_name }}</p>
      <p><span>Valutazione: </span>{{ serie.vote_average }}</p>
      <p>
        <span>Lingua: </span>
        <img
          class="lang-flag"
          :src="getFlag(serie.original_language)"
          :alt="serie.original_language"
          @error="fixImgError($event)"
        />
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "SeriesListComponent",

  props: {
    series: Array,
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

    fixThumbError(event) {
      event.target.src = `https://us.123rf.com/450wm/pavelstasevich/pavelstasevich1811/pavelstasevich181101028/112815904-no-image-available-icon-flat-vector-illustration.jpg?ver=6`;
    },
  },
};
</script>

<style lang="scss" scoped>
.series-container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
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