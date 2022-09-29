<template>
  <div id="app">
    <HeaderComponent />
    <MainComponent />
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
      queryText: "",
      movies: [],
    };
  },

  components: {
    HeaderComponent,
    MainComponent,
  },

  mounted() {
    this.generateFromApi("bello");
  },

  methods: {
    generateFromApi(searchText) {
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=${apiKeyVS}&query=${searchText}&language=it-IT`
        )
        .then((response) => {
          console.log(response);
          if (response.status === 200) {
            this.movies = response.data.results;
          }
        })
        .catch((error) => {
          console.log(error.message);
        });
    },
  },
};
</script>

<style lang="scss">
@import "@/assets/css/generics.scss";
</style>

