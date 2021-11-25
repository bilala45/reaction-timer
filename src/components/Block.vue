<template>
  <button class="reaction">Click me!</button>
</template>

<script>
export default {
  props: ["time"],
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