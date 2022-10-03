<template>
  <div v-if="activeScreen === true" class="login-screen-container">
    <div class="login-options-container">
      <h1>Chi vuole guardare Boolflix?</h1>
      <div class="users">
        <div @click="switchActiveLoginScreen" class="single-user">
          <img src="https://i.ibb.co/fqjLWsd/Testa-failah-rosa.png" alt="" />
          <h5>Valerio</h5>
        </div>
        <div @click="switchActiveLoginScreen" class="single-user">
          <img src="http://puu.sh/Job3Q/84afadaed7.jpg" alt="" />
          <h5>Jack Sparrow</h5>
        </div>
        <div @click="switchActiveLoginScreen" class="single-user">
          <img
            src="https://i.pinimg.com/originals/dc/ab/b7/dcabb7fbb2f763d680d20a3d228cc6f9.jpg"
            alt=""
          />
          <h5>Pikachu</h5>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "LoginScreenComponent",

  data() {
    return {
      activeScreen: true,
    };
  },

  methods: {
    switchActiveLoginScreen() {
      console.log("Mi hai cliccato");
      setTimeout(this.switchToFalse, 600);
    },

    switchToFalse() {
      this.activeScreen = !this.activeScreen;
    },
  },
};
</script>

<style lang="scss" scoped>
.login-screen-container {
  background-color: #141414;
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 5000;

  .login-options-container {
    width: 70%;
    margin: 0 auto;
    color: white;

    h1 {
      text-align: center;
      font-size: 4rem;
      font-weight: 100;
      margin-bottom: 80px;
    }

    .users {
      display: flex;
      justify-content: center;
      column-gap: 10%;

      .single-user {
        width: 10vw;
        cursor: pointer;

        &:hover h5 {
          color: white;
        }

        &:hover img {
          outline: 4px solid white;
        }
      }

      img {
        width: 10vw;
        height: 10vw;
        border-radius: 5px;
      }

      h5 {
        text-align: center;
        color: #7f7f7f;
        font-size: 1.6rem;
        font-weight: 100;
        margin-top: 10px;
      }
    }
  }
}
</style>