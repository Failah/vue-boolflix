<template>
  <div id="movies-container">
    <HorizontalSlidersComponent @slideRight="slideRight" />
    <h2>Lista dei Film:</h2>
    <div class="card-container">
      <div
        class="card"
        :class="{ 'slide-right': slideRightValue }"
        v-for="movie in movies"
        :key="movie.id"
      >
        <div class="image-container">
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
        <p class="overview">
          <span>Overview:</span>
          <span>{{ movie.overview }}</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import StarsValutationComponent from "@/components/StarsValutationComponent.vue";
import LanguageFlagComponent from "@/components/LanguageFlagComponent.vue";
import HorizontalSlidersComponent from "@/components/HorizontalSlidersComponent.vue";

export default {
  name: "MoviesListComponent",

  data() {
    return {
      vote: "",
      slideRightValue: false,
    };
  },

  props: {
    movies: Array,
  },

  components: {
    StarsValutationComponent,
    LanguageFlagComponent,
    HorizontalSlidersComponent,
  },

  methods: {
    fixThumbError(event) {
      event.target.src = `https://i.ibb.co/5WrL0PB/noimageava-372x558.webp`;
    },

    slideRight() {
      console.log("slide right");
      this.slideRightValue = !this.slideRightValue;
    },
  },
};
</script>

<style lang="scss" scoped>
.slide-right {
  animation-name: slideright;
  animation-duration: 0.8s;
  animation-fill-mode: forwards;
}

@keyframes slideright {
  from {
    left: 0;
  }
  to {
    left: -1200px;
  }
}

#movies-container {
  max-width: 1800px;
  margin: 0 auto;
  position: relative;

  .card-container {
    display: flex;
    flex-wrap: nowrap;
    column-gap: 20px;
    overflow-x: auto;
    left: 0;
  }

  h2 {
    width: 100%;
    margin-top: 30px;
    margin-bottom: 20px;
    text-decoration: underline;
    font-size: 2.5rem;
  }

  .card {
    // border: 1px solid grey;
    border-radius: 8px;
    min-width: calc(100% / 6 - 20px);
    height: 421px;
    margin-bottom: 20px;
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    cursor: pointer;

    &:hover .image-container {
      display: none;
    }

    .image-container {
      position: absolute;

      img {
        border-radius: 8px;
      }
    }

    p {
      margin-top: 5px;
    }

    .overview {
      max-height: 250px;
      overflow-y: auto;
    }

    .overview::-webkit-scrollbar {
      display: none;
    }
  }
}
</style>