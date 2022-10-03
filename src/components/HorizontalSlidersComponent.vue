<template>
  <div class="arrows">
    <div class="left-arrow">LEFT</div>
    <div @click="$emit('slideRight')" class="right-arrow">RIGHT</div>
  </div>
</template>

<script>
export default {
  name: "HorizontalSlidersComponent",
};
</script>

<style lang="scss" scoped>
.arrows {
  display: flex;
  justify-content: space-between;
  max-width: 1200px;
  width: 100%;
  position: absolute;
  top: 40%;

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