<template>
  <div class="child">
    <h3>我是子组件</h3>
    <h3>{{ car.name }}---{{ car.price }}</h3>
    <Son />
  </div>
</template>

<script>
import Son from "./Son.vue";
import { inject } from "vue";
export default {
  components: { Son },
  setup() {
    let car = inject("car");
    return {
      car,
    };
  },
};
</script>
 
<style>
.child {
  padding: 10px;
  background: rgb(255, 95, 47);
  height: 200px;
  width: 100%;
}
</style>