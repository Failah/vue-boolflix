<template>
  <div class="header-container">
    <div class="boolzap-options">
      <h2>BOOLFLIX</h2>
      <div><a href=".">Home</a></div>
      <div><a href="#series-container">Serie TV</a></div>
      <div><a href="#movies-container">Film</a></div>
      <div @click="$emit('searchPopular')">Popolari</div>
    </div>

    <!-- Old search bar (still working if abled) -->
    <!-- <div>
      <input
        type="text"
        v-model="inputText"
        @keyup.enter="$emit('search', inputText)"
        placeholder="Cerca film o serie tv"
      />
      <button @click="$emit('search', inputText)">CERCA</button>
    </div> -->

    <div id="header-right-options">
      <div class="search">
        <i @click="toggleSearchInput" class="fa-solid fa-magnifying-glass"></i>
        <input
          v-model="inputText"
          @keyup.enter="$emit('search', inputText)"
          :class="{ toggle: toggleIndex === true }"
          class="input"
          type="text"
          placeholder="Titoli, persone, generi"
        />
      </div>
      <i class="fa-solid fa-bell"></i>
      <div class="user-header-manage">
        <div>
          <img src="https://i.ibb.co/fqjLWsd/Testa-failah-rosa.png" alt="" />
        </div>
        <i class="fa-solid fa-caret-down"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderComponent",

  data() {
    return {
      inputText: "",
      toggleIndex: false,
    };
  },

  methods: {
    toggleSearchInput() {
      console.log("search input clicked");
      this.toggleIndex = !this.toggleIndex;
    },
  },
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

  i {
    font-size: 1.4rem;
  }

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

#header-right-options {
  display: flex;
  align-items: center;

  > i {
    cursor: pointer;
  }

  .search {
    right: 15px;
    position: relative;
    display: inline-block;
    background-color: #0b0b0b;

    input {
      width: 0px;
      height: 34px;
      background-color: #0b0b0b;
      box-shadow: none;
      color: #fff;
      border: 1px solid transparent;
      outline: none;
      padding-left: 35px;
      font-size: 16px;
      transition: 0.3s ease all;

      &.toggle {
        width: 240px;
        border-color: #fff;
      }
    }

    i {
      width: 18px;
      left: 8px;
      top: 50%;
      transform: translateY(-50%);
      position: absolute;
      cursor: pointer;
      font-size: 1.4rem;
    }
  }

  .user-header-manage {
    display: flex;
    align-items: center;
    column-gap: 0.5vw;
    margin-left: 20px;
    margin-right: 12px;
    cursor: pointer;

    i {
      font-size: 0.9rem !important;
      cursor: pointer;
    }

    img {
      width: 28px;
      height: 28px;
      border-radius: 3px;
      cursor: pointer;
    }
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