<template>
  <div class="container">
    <div
      class="alert alert-success fw-bold mx-auto rounded pt-3"
      v-if="showBlock"
      @click="stopTimer"
      style="width: 300px; height: 200px"
    >
      Click Here - {{ delay }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showBlock: false,
      score: 0,
      timer: null,
    };
  },
  props: ["delay"],
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.score += 50;
      }, 50);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("endGame", this.score);
    },
  },
};
</script>

<style>
</style>