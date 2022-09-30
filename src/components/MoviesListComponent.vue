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
        <StarsValutationComponent :voteInteger="movie.vote_average" />
      </p>
      <p>
        <span>Lingua: </span>
        <LanguageFlagComponent :flagLanguage="movie.original_language" />
      </p>
    </div>
  </div>
</template>

<script>
import StarsValutationComponent from "@/components/StarsValutationComponent.vue";
import LanguageFlagComponent from "@/components/LanguageFlagComponent.vue";

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

  components: {
    StarsValutationComponent,
    LanguageFlagComponent,
  },

  methods: {
    fixThumbError(event) {
      event.target.src = `https://i.ibb.co/5WrL0PB/noimageava-372x558.webp`;
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
</style>