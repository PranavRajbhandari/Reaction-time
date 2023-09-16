<template>
  <h1>Human Reaction Time</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay ="delay" @end="endGame"/>
  <!-- this @end is imported from block by$emit which means we can send component from child to parent -->
  <Results v-if="showResult" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue';
export default {
  
  components: {
      Block, Results
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult:false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
        this.isPlaying = true
        console.log(this.delay)
        this.showResult = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    }
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
