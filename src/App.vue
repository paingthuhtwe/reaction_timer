<template>
  <div class="container">
    <div class="alert alert-primary">
      <h1 class="alert alert-success fw-bold">How fast can you catch me?</h1>
      <button
        class="btn btn-outline-success fw-bold"
        :disabled="isPlaying"
        @click="start"
      >
        Play
      </button>
      <div class="mt-3" v-if="isPlaying">
        <BlockPage :delay="delay" @endGame="endGame"></BlockPage>
      </div>
      <div v-if="end">
        <ResultPage :score="score"></ResultPage>
      </div>
    </div>
  </div>
</template>

<script>
import ResultPage from "./components/ResultPage.vue";
import BlockPage from "./components/BlockPage.vue";

export default {
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: 0,
      end: false,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      this.end = false;
    },
    endGame(score) {
      this.score = score;
      this.isPlaying = false;
      this.end = true;
    },
  },
  name: "App",
  components: {
    BlockPage,
    ResultPage,
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
