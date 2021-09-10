<template>
  <div>
    <Header />

    <Guesses
      :shuffled-colors="shuffledColors"
      :show-results="showResults"
      @new-game="startAgain"
    />

    <HiddenColors
      :shuffled-colors="shuffledColors"
    />

    <ColorsPanel
      :colors-in-circles="colorsInCircles"
      @selected-color="addColorsToArr"
      @changeColorinButton="changeColorinButton"
    />

  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import ColorsPanel from "@/components/ColorsPanel.vue";
import HiddenColors from "@/components/HiddenColors.vue";
import Guesses from "@/components/Guesses.vue";

export default {
  name: "App",
  components: {
    Header,
    ColorsPanel,
    HiddenColors,
    Guesses,
  },
  data() {
    return {
      shuffledColors: [],
      chosenColors: [],
      showResults: false,
      colorsInCircles: [
        { color: "blue", correctColor: false },
        { color: "green", correctColor: false },
        { color: "black", correctColor: false },
        { color: "grey", correctColor: false },
        { color: "pink", correctColor: false },
        { color: "yellow", correctColor: false },
        { color: "red", correctColor: false },
        { color: "purple", correctColor: false },
        { color: "orange", correctColor: false },
        { color: "tan", correctColor: false },
        { color: "violet", correctColor: false },
        { color: "turquoise", correctColor: false },
      ],
    };
  },
  methods: {
    mixArrColors() {
      this.shuffledColors = this.colorsInCircles.map((i) => i);
      this.shuffledColors.sort(() => Math.random() - 0.5).splice(0, 8);
      return this.shuffledColors;
    },

    addColorsToArr(color) {
      if (this.chosenColors.length <= 3) {
        //it adds the colors chosen by the user to the array
        this.chosenColors.push({ color: color });

        //it makes appear the results once the user has chosed 4 colors
        if (this.chosenColors.length === 4) {
          this.showResults = true;
        }
      }
    },

    changeColorinButton(color) {
      for (let index = 0; index < this.shuffledColors.length; index++) {
        if (this.shuffledColors[index].color === color) {
          this.shuffledColors[index].correctColor = true;
        }
      }
    },

    startAgain() {
      this.showResults = false;
      this.shuffledColors.map(e => e.correctColor = false)
      this.chosenColors = [];
      this.$nextTick().then(this.mixArrColors);
    },
  },

  mounted() {
    this.$nextTick().then(this.mixArrColors);
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
