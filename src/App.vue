<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <AppBlock v-if="isPlaying" :delay="delay" @end="endGame" />
  <AppResults v-if="showResults" :score="score" />
</template>

<script>
// when the game ends, show the results component
// output the score inside the results component

import AppBlock from './components/AppBlock.vue'
import AppResults from './components/AppResults.vue'

export default {
  name: 'App',
  components: { AppBlock, AppResults },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      // set time amount (ms)
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #444;
    margin-top: 60px;
  }
  button {
    background: #0faf87;
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    font-size: 16px;
    letter-spacing: 1px;
    cursor: pointer;
    margin: 10px;
  }
  button[disabled] {
    opacity: 0.2;
    cursor: not-allowed;
  }
</style>
