<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h1>Test Reaction Time</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Result :score="score" v-if="showResult" />
</template>

<script>
import Block from './components/Block.vue';
import Result from './components/Result.vue';

export default {
  name: 'App',
  components: {
    Block, Result
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods: {
    start() {
      this.delay = 1000 + Math.floor(Math.random() * 5000);
      this.isPlaying = true;
      this.showResult = false;
      // console.log(this.delay)
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
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
  font-style: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button:disabled {
  background: #999;
  cursor: not-allowed;
}
</style>
