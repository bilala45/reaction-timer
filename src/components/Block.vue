<template>
  <!-- component renders if showBlock is true -->
  <button class="reaction" v-if="showBlock">Click me!</button>
</template>

<script>
export default {
  // props specified in parent component
  props: ["time"],

  // component data
  data() {
    return {
      showBlock: false,
    };
  },

  // life cycle hook that fires when component is mounted
  mounted() {
    // set a timeout equal to the random time generated
    // change showBlock to true after the time passes (button will appear on the screen)
    setTimeout(() => {
      this.showBlock = true;
      console.log(this.time);
    }, this.time);
  },
};
</script>

<style>
.reaction {
  background-color: #12a5a5;
  border: none;
  color: white;
  margin-top: 100px;
  padding: 50px 100px;
  border-radius: 10px;
  text-transform: uppercase;
}

.reaction:hover {
  cursor: pointer;
}
</style>