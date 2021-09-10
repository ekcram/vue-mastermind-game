<template>
  <div class="guesses-container" v-if="showResults">
    <h3>Results</h3>
    <div
      v-for="(ele, index) in shuffledColors"
      :key="index"
      @load="mixArrColors(ele.color)"
      :style="{ 'background-color': ele.color }"
      class="color-circle"
    ></div>
    <div>
      <button @click="$emit('new-game')" class="button-start-again">
        Start again
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    shuffledColors: Array,
    showResults: {
      type: Boolean,
      required: true,
      default: false,
    },
  },
};
</script>

<style>
</style>