<template>
  <!-- component renders if showBlock is true -->
  <!-- timer begins atutomatically after block appears and stops when block is clicked -->
  <button class="reaction" v-if="showBlock" @click="stopTimer">
    Click me!
  </button>
</template>

<script>
export default {
  // props specified in parent component
  props: ["time"],

  // component data
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },

  // life cycle hook that fires when component is mounted
  mounted() {
    // set a timeout equal to the random time generated
    // change showBlock to true after the time passes (button will appear on the screen)
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.time);
  },

  methods: {
    // function that runs after the user starts the game
    startTimer() {
      // callback function runs every 10 ms (updates reaction time)
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },

    // stops execution of setInterval
    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTime);
      this.$emit("recordTime", this.reactionTime);
    },
  },
};
</script>

<style>
.reaction {
  background-color: #12a5a5;
  border: none;
  color: white;
  margin-top: 50px;
  padding: 50px 100px;
  border-radius: 10px;
  text-transform: uppercase;
}

.reaction:hover {
  cursor: pointer;
}
</style>