<template>
  <h1 class="app-title">Ninja Reaction Timer</h1>
  <button class="play-btn" @click="startGame" :disabled="isPlaying">
    play
  </button>
  <Results v-if="showResults" :score="score" />
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
</template>

<script>
import Block from "./components/Block";
import Results from "./components/Results";

export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    startGame() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    },
  },
};
</script>

<style>
/* Default */
html {
  box-sizing: border-box;
  font-size: 16px;
  scroll-behavior: smooth;
}
body {
  min-height: 100vh;
  display: flex;
  justify-content: center;
}
*,
*::before,
*::after {
  box-sizing: inherit;
  margin: 0;
  padding: 0;
}
/* Variables */
:root {
  --black: rgba(20, 20, 20, 1);
  --green: rgba(0, 194, 140, 1);
  --grey: rgba(150, 150, 150, 1);
}
/* App */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeSpeed;
  line-height: 1.5;
  width: 100%;
  max-width: 960px;
  text-align: center;
  margin-top: 3rem;
}
.app-title {
  color: var(--black);
}
.play-btn {
  border: 2px solid var(--green);
  outline: none;
  background: none;
  color: var(--green);
  padding: 7px 10px;
  font-size: 1rem;
  border-radius: 5px;
  font-weight: bold;
  cursor: pointer;
  margin-top: 1.5rem;
}
.play-btn:disabled {
  border-color: var(--grey);
  color: var(--grey);
  cursor: not-allowed;
}
</style>
