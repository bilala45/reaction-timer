<template>
  <p class="result">Reaction time: {{ score }} ms</p>
</template>

<script>
export default {
  props: ["score"],
};
</script>

<style>
.result {
  margin-top: 100px;
  font-size: 30px;
}
</style>