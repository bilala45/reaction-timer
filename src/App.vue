<template>
  <!-- title -->
  <h1>Reaction Timer</h1>

  <!-- button to start game -->
  <!-- add attribute to disable button when user is playing -->
  <button @click="startGame" class="play" :disabled="isPlaying">play</button>
  <br />

  <!-- display Block component when isPlaying is true (when user is playing game) -->
  <!-- dynamically bind time to time attribute  -->
  <!-- custom event from child Block that calls endGame method -->
  <Block v-if="isPlaying" :time="time" @recordTime="endGame" />

  <!-- bind score as a prop to Results template -->
  <Results v-if="score" :score="score" />
</template>

<script>
// import child Vue components
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",

  // imported child Vue components
  components: { Block, Results },

  // data attributes (must be in a data function)
  data() {
    return {
      // records if user is currently playing
      isPlaying: false,
      // records delay before block appears
      time: null,
      score: null,
    };
  },

  methods: {
    // method to run when user clicks button to play game
    startGame() {
      // set isPlaying to true
      this.isPlaying = true;
      // set score back to null
      this.score = null;
      // generate a random number between 2-5 that will be our game delay
      this.time = Math.round(2000 + Math.random() * 3000);
    },

    // takes in reactionTime, which is emitted by the Block child component
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
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
  color: #2c3e50;
  margin-top: 60px;
}

/* play button styles */
.play {
  background-color: #12a5a5;
  border: none;
  color: white;
  padding: 10px 20px;
  border-radius: 10px;
  text-transform: uppercase;
}

.play:hover {
  cursor: pointer;
}

.play:disabled {
  background-color: #12a5a571;
}

.play:disabled:hover {
  cursor: not-allowed;
}
</style>