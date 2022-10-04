<template>
  <div id="series-container">
    <h2>Lista delle serie TV:</h2>
    <div class="card-container">
      <div class="card" v-for="serie in series" :key="serie.id">
        <div class="image-container">
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
          <StarsValutationComponent :voteInteger="serie.vote_average" />
        </p>
        <p>
          <span>Lingua: </span>
          <LanguageFlagComponent :flagLanguage="serie.original_language" />
        </p>
        <p class="overview">
          <span>Overview:</span>
          <span>{{ serie.overview }}</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import StarsValutationComponent from "@/components/StarsValutationComponent.vue";
import LanguageFlagComponent from "@/components/LanguageFlagComponent.vue";

export default {
  name: "SeriesListComponent",

  props: {
    series: Array,
  },

  components: {
    StarsValutationComponent,
    LanguageFlagComponent,
  },

  methods: {
    fixThumbError(event) {
      event.target.src = `https://i.ibb.co/5WrL0PB/noimageava-372x558.webp`;
    },
  },
};
</script>

<style lang="scss" scoped>
#series-container {
  max-width: 1800px;
  margin: 0 auto;
  margin-bottom: 80px;

  .card-container {
    display: flex;
    flex-wrap: nowrap;
    column-gap: 20px;
    overflow-x: auto;
  }

  h2 {
    width: 100%;
    margin-top: 30px;
    margin-bottom: 20px;
    text-decoration: underline;
    font-size: 2.5rem;
  }

  .card {
    border: 1px solid grey;
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
    }

    p {
      margin-top: 5px;
    }

    .overview {
      max-height: 250px;
      overflow-y: auto;
    }
  }
}

.lang-flag {
  width: 20px;
}
</style>