<template>
  <div>
    <h3>Choose 4 colors</h3>
    <div
      v-for="(circle, index) in colorsInCircles"
      :key="index"
      class="color-circle"
      @click="$emit('selected-color', circle.color); $emit('changeColorinButton', circle.color)"
      :style="{ 'background-color': circle.color }"
    ></div>
  </div>
</template>

<script>
export default {
  name: "ColorsPanel",
  props: {
    colorsInCircles: Array
  },
};
</script>

<style>
</style>