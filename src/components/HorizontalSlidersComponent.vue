<template>
  <div class="arrows">
    <div class="left-arrow"><i class="fa-solid fa-chevron-left"></i></div>
    <div @click="$emit('slideRight')" class="right-arrow">
      <i class="fa-solid fa-chevron-right"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "HorizontalSlidersComponent",
};
</script>

<style lang="scss" scoped>
.arrows {
  display: none;
  justify-content: space-between;
  max-width: 1200px;
  width: 100%;
  position: absolute;
  top: 50%;

  .left-arrow,
  .right-arrow {
    color: grey;
    font-weight: bold;
    font-size: 3rem;
    z-index: 1000;
    cursor: pointer;
  }
}
</style>