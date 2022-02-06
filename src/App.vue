<template>
    <h1>Reaction timer</h1>
    <button @click="startGame" :disabled="isPlaying" class="play-btn">Play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Results v-if="showResults" :score="score"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
      Block,
      Results
  },
  data() {
    return {
      isPlaying: false,
      maxMS: 3000,
      startingMS: 2000,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    startGame() {
      this.isPlaying = true
      this.showResults = false
      this.delay = this.startingMS + Math.random() * this.maxMS
    },
    endGame(reactionTime) {
      this.isPlaying = false
      this.score = reactionTime
      this.showResults = true
    }
  }
}
</script>

<style>
  #app {
    font-family: 'Short Stack', cursive;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  h1 {
    margin-bottom: 3rem;
  }
  .play-btn {
    padding: 0.6rem 2rem;
    font-family: 'Short Stack', cursive;
    font-size: 1.1rem;
    background-color: rgba(255,255,255,0.2);
    border-radius: 0.5rem;
    border-color: rgba(0,0,0,0.2);
    color: #2c3e50;    
    cursor: pointer;
  }
  .play-btn:disabled{
    opacity: 0.5;
    cursor: default;
    color: #ffffff;
  }
</style>
