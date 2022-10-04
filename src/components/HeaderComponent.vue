<template>
  <div class="header-container">
    <div class="boolzap-options">
      <h2>BOOLFLIX</h2>
      <div><a href=".">Home</a></div>
      <div><a href="#series-container">Serie TV</a></div>
      <div><a href="#movies-container">Film</a></div>
      <div @click="$emit('searchPopular')">Popolari</div>
    </div>

    <div class="search">
      <input class="input" type="text" placeholder="Titles, people, genres" />
      <img
        class="img"
        src="https://static.vecteezy.com/system/resources/previews/000/442/657/non_2x/vector-search-icon.jpg"
        alt=""
      />
    </div>

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
  max-width: 1800px;
  margin: 0 auto;
  background-color: #0b0b0b;
  color: white;
  height: 8vh;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;

  .boolzap-options {
    display: flex;
    align-items: center;
    column-gap: 15px;

    a {
      color: white;
      text-decoration: none;
    }

    div {
      cursor: pointer;
    }
  }

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

.boolzap-options div:hover {
  transition: color 0.3s linear;
  color: rgb(179, 176, 176);
}

.boolzap-options div:hover a {
  transition: color 0.3s linear;
  color: rgb(179, 176, 176);
}
</style>