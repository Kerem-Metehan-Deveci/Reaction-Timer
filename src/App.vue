<template>
<h1>Reaction Timer - Kerem Metehan Deveci</h1>
<button @click="start" :disabled="isPlaying">Play</button>
<VBlock v-if="isPlaying" :delay="delay" @end="endGame" />
<VResults v-if="showResults" :score="score" />
</template>

<script>
import VBlock from './components/VBlock.vue'
import VResults from './components/VResults.vue'


export default {
  name: 'App',
  components: { VBlock, VResults },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    start() {
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
  background: rgb(34,193,195);
  background: linear-gradient(0deg, rgba(34,193,195,1) 0%, rgba(253,187,45,1) 100%);
  color: white;
  border: solid 1px;
  padding: 8px 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
  border-radius: 10px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
