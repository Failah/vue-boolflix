<template>
  <div class="header-container">
    <div>
      <input type="text" v-model="inputText" />
      <button @click="$emit('search', inputText)">RICERCA</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderComponent",

  data() {
    return {
      inputText: "",
    };
  },

  methods: {},
};
</script>

<style lang="scss" scoped>
.header-container {
  background-color: #0b0b0b;
  color: white;
  height: 8vh;
}
</style>