<template>
  <h2>{{ sum }}</h2>
  <button @click="sum++">sum++</button>
  <br />
</template>

<script>
import { ref } from "vue";
export default {
  name: "App",
  components: {},

  setup() {
    let sum = ref(0);
    return {
      sum,
    };
  },
};
</script>

<style>
</style>
