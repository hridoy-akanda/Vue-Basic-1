<template>
  <h2>Reaction Timer</h2>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Result v-if="showResult" :score="score" />
  <Block v-if="isPlaying" :delay="delay" @stop="end" />
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";
export default {
  name: "App",
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      showResult: false,
      score: null,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 3000;
      this.showResult = false;
    },
    end(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
    },
  },
};
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
  width: 80px;
  height: auto;
  border: none;
  background-color: green;
  color: white;
  padding: 10px;
  border-radius: 5px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
