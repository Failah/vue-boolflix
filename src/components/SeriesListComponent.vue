<template>
  <div class="series-container">
    <div class="card" v-for="serie in series" :key="serie.id">
      <div>{{ serie.name }}</div>
      <p>{{ serie.original_name }}</p>
      <p>{{ serie.vote_average }}</p>
      <p>
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
.series-container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  column-gap: 20px;

  .card {
    border: 1px solid grey;
    width: calc(20% - 20px);
  }
}

.lang-flag {
  width: 20px;
}
</style>