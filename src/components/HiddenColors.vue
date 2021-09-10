
<template>
  <div>
    <h3>Can you guess the colors hidden in each button?</h3>
    <h4>Tip: There can be repeated colors!</h4>
    <div
      v-for="(ele, index) in shuffledColors"
      :key="index"
      @load="mixArrColors(ele.color)"
      v-bind:class="[ele.correctColor ? 'white' : 'button']">
      {{index + 1}}
     
    </div>
  </div>
</template>

<script>
export default {
  name: "HiddenColors",
  props: {
    shuffledColors: Array
  },
};
</script>

