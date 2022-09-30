<template>
  <div class="stars-container">
    <span
      v-if="
        voteDecimalConverter(voteInteger) === 1 ||
        voteDecimalConverter(voteInteger) === 0
      "
      ><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i
      ><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i
      ><i class="fa-regular fa-star"></i
    ></span>
    <span v-if="voteDecimalConverter(voteInteger) === 2"
      ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
      ><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i
      ><i class="fa-regular fa-star"></i
    ></span>
    <span v-if="voteDecimalConverter(voteInteger) === 3"
      ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
      ><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i
      ><i class="fa-regular fa-star"></i
    ></span>
    <span v-if="voteDecimalConverter(voteInteger) === 4"
      ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
      ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
      ><i class="fa-regular fa-star"></i
    ></span>
    <span v-if="voteDecimalConverter(voteInteger) === 5"
      ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
      ><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i
      ><i class="fa-solid fa-star"></i
    ></span>
  </div>
</template>

<script>
export default {
  name: "StarsValutationComponent",

  props: {
    voteInteger: Number,
  },

  methods: {
    voteDecimalConverter(value) {
      let convertedValue = Math.ceil(value / 2);
      return convertedValue;
    },
  },
};
</script>

<style lang="scss" scoped>
.stars-container {
  display: inline-block;
}
</style>