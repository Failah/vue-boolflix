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
      <p>
        <span>Valutazione: </span>
        <span
          v-if="
            voteDecimalConverter(serie.vote_average) === 1 ||
            voteDecimalConverter(serie.vote_average) === 0
          "
          ><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i
          ><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i
          ><i class="fa-regular fa-star"></i
        ></span>
        <span v-if="voteDecimalConverter(serie.vote_average) === 2"
          ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
          ><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i
          ><i class="fa-regular fa-star"></i
        ></span>
        <span v-if="voteDecimalConverter(serie.vote_average) === 3"
          ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
          ><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i
          ><i class="fa-regular fa-star"></i
        ></span>
        <span v-if="voteDecimalConverter(serie.vote_average) === 4"
          ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
          ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
          ><i class="fa-regular fa-star"></i
        ></span>
        <span v-if="voteDecimalConverter(serie.vote_average) === 5"
          ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
          ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
          ><i class="fa-solid fa-star"></i
        ></span>
      </p>
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
      event.target.src = `https://i.ibb.co/5WrL0PB/noimageava-372x558.webp`;
    },

    voteDecimalConverter(value) {
      let convertedValue = Math.ceil(value / 2);
      return convertedValue;
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
    margin-top: 30px;
    margin-bottom: 20px;
    text-decoration: underline;
    font-size: 2.5rem;
  }

  .card {
    border: 1px solid grey;
    width: calc(100% / 4 - 20px);
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