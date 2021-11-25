<template>
  <h1>Reaction Timer</h1>
  <button @click="console.log('bro')" class="play">play</button>
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: {
    Block,
    Results,
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

.play {
  background-color: #12a5a5;
  border: none;
  color: white;
  padding: 10px 20px;
  border-radius: 10px;
  text-transform: uppercase;
}
</style>
