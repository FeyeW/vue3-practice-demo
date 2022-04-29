<template>
  <div class="son">
    <h3>我是孙组件</h3>
    <h4>{{ car.name }}---{{ car.price }}</h4>
  </div>
</template>

<script>
import { inject } from "vue";
export default {
  setup() {
    let car = inject("car");
    return {
      car,
    };
  },
};
</script>
   
<style>
.son {
  padding: 10px;
  background: greenyellow;
  height: 120px;
  width: 100%;
}
</style>