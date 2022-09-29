<template>
  <div class="header-container">
    <h2>BOOLZAP</h2>
    <div>
      <input
        type="text"
        v-model="inputText"
        @keyup.enter="$emit('search', inputText)"
        placeholder="Cerca film o serie tv"
      />
      <button @click="$emit('search', inputText)">CERCA</button>
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
  max-width: 1200px;
  margin: 0 auto;
  background-color: #0b0b0b;
  color: white;
  height: 8vh;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;

  h2 {
    color: red;
  }

  input {
    margin-right: 15px;
    outline: none;
  }

  button {
    padding: 3px 15px;
    cursor: pointer;
  }
}

// effects
button:active {
  transform: scale(0.95);
}
</style>