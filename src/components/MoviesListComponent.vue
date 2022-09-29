<template>
  <div class="movies-container">
    <h2>Lista dei Film:</h2>
    <div class="card" v-for="movie in movies" :key="movie.id">
      <div>
        <img
          :src="'https://image.tmdb.org/t/p/w342' + movie.poster_path"
          alt=""
          @error="fixThumbError($event)"
        />
      </div>
      <div><span>Titolo: </span>{{ movie.title }}</div>
      <p><span>Titolo Originale: </span>{{ movie.original_title }}</p>
      <p>
        <span>Valutazione: </span>
        <span
          v-if="
            voteDecimalConverter(movie.vote_average) === 1 ||
            voteDecimalConverter(movie.vote_average) === 0
          "
          ><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i
          ><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i
          ><i class="fa-regular fa-star"></i
        ></span>
        <span v-if="voteDecimalConverter(movie.vote_average) === 2"
          ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
          ><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i
          ><i class="fa-regular fa-star"></i
        ></span>
        <span v-if="voteDecimalConverter(movie.vote_average) === 3"
          ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
          ><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i
          ><i class="fa-regular fa-star"></i
        ></span>
        <span v-if="voteDecimalConverter(movie.vote_average) === 4"
          ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
          ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
          ><i class="fa-regular fa-star"></i
        ></span>
        <span v-if="voteDecimalConverter(movie.vote_average) === 5"
          ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
          ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
          ><i class="fa-solid fa-star"></i
        ></span>
      </p>
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

  data() {
    return {
      vote: "",
    };
  },

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

    fixThumbError(event) {
      event.target.src = `https://i.ibb.co/5WrL0PB/noimageava-372x558.webp`;
    },

    voteDecimalConverter(value) {
      let convertedValue = Math.ceil(value / 2);
      return convertedValue;
    },

    // displays actual html code in the DOM and not the icons, needs more investigation
    convertIntegerToStar(integer) {
      let starValue = "";

      switch (integer) {
        case 1: {
          starValue = `<i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i>`;
          break;
        }
        case 2: {
          starValue = `<i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i>`;
          break;
        }
        case 3: {
          starValue = `<i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i>`;
          break;
        }
        case 4: {
          starValue = `<i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i>`;
          break;
        }
        case 5: {
          starValue = `<i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i>`;
          break;
        }
      }

      //   let stars = document.createElement("div");
      //   let starsNumber = document.createTextNode(starValue);

      //   stars.appendChild(starsNumber);

      //   console.log(stars);

      return starValue;
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