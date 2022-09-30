<template>
  <div id="app">
    <HeaderComponent @search="searchStart" />
    <MainComponent :movies="movies" :series="series" />
  </div>
</template>

<script>
import HeaderComponent from "@/components/HeaderComponent.vue";
import MainComponent from "@/components/MainComponent.vue";

import axios from "axios";
import { apiKeyVS } from "@/env";

export default {
  name: "App",

  data() {
    return {
      movies: [],
      series: [],
      queryText: "",
    };
  },

  components: {
    HeaderComponent,
    MainComponent,
  },

  // just generate something "random" to display when the page is refreshed
  created() {
    let randomLetters = ["la", "di", "da", "lo", "bel", "do", "le"];
    let index =
      randomLetters[Math.floor(Math.random() * randomLetters.length + 1)];
    this.searchStart(index);
  },

  methods: {
    generateFromApi(searchText) {
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=${apiKeyVS}&query=${searchText}&language=it-IT`
        )
        .then((response) => {
          console.log("Movies:", response);
          if (response.status === 200) {
            this.movies = response.data.results;
          }
        })
        .catch((error) => {
          console.log(error.message);
        });

      axios
        .get(
          `https://api.themoviedb.org/3/search/tv?api_key=${apiKeyVS}&query=${searchText}&language=it-IT`
        )
        .then((response) => {
          console.log("Series:", response);
          if (response.status === 200) {
            this.series = response.data.results;
          }
        })
        .catch((error) => {
          console.log(error.message);
        });
    },

    searchStart(inputText) {
      this.queryText = inputText;
      this.generateFromApi(this.queryText);
    },
  },
};
</script>

<style lang="scss">
@import "@/assets/css/generics.scss";

#app {
  background-color: #0b0b0b;
  height: 100vh;
  overflow: hidden;
}
</style>

