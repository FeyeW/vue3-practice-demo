<template>
  <h2>{{ sum }}</h2>
  <button @click="sum++">sum++</button>
  <br />
  <h2>当前点击时鼠标的坐标为：x:{{ point.x }},y:{{ point.y }}</h2>
</template>

<script>
import { ref } from "vue";
import usePonit from "../hook/usePoint";
export default {
  name: "App",
  components: {},

  setup() {
    let sum = ref(0);
    const point = usePonit();
    return {
      sum,
      point,
    };
  },
};
</script>

<style>
</style>
