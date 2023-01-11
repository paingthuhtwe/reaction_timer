<template>
  <p class="alert alert-success mt-3 fw-bold">Result is : {{ score }}ms</p>
  <div v-if="score < 250">
    <p class="alert alert-success">You are too fast!</p>
  </div>
  <div v-else-if="score > 250 && score < 500">
    <p class="alert alert-warning">You are nomal!</p>
  </div>
  <div v-else><p class="alert alert-danger">You are too slow!</p></div>
</template>

<script>
export default {
  props: ["score"],
};
</script>

<style>
</style>