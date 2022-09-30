<template>
  <span>
    <img
      class="lang-flag"
      :src="getFlag(flagLanguage)"
      :alt="flagLanguage"
      @error="fixImgError($event)"
    />
  </span>
</template>

<script>
export default {
  name: "LanguageFlagComponent",

  props: {
    flagLanguage: String,
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
        case "hi": {
          country = "in";
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
.lang-flag {
  width: 20px;
}
</style>