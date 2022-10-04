<template>
  <div v-if="netflixLogoValue" id="netflix-loading-screen">
    <img src="..\src\assets\netflixLoading.gif" alt="" />
  </div>
</template>

<script>
export default {
  name: "NetflixLoadScreenComponent",

  data() {
    return {
      netflixLogoValue: true,
    };
  },

  created() {
    setTimeout(this.switchNetflixLogoValue, 3500);
  },

  methods: {
    switchNetflixLogoValue() {
      this.netflixLogoValue = !this.netflixLogoValue;
      console.log("switch netflix logo value");
    },
  },
};
</script>

<style lang="scss" scoped>
#netflix-loading-screen {
  height: 100vh;
  width: 100vw;
  background-color: #141414;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 10000;
  display: flex;
  justify-content: center;
  align-items: center;

  img {
    width: 930px;
    // height: 500px;
  }
}
</style>