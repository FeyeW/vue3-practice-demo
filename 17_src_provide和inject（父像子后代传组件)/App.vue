<template>
  <div class="app">
    <h3>我是父组件</h3>
    <h3>{{ name }}---{{ price }}</h3>
    <Child> </Child>
  </div>
</template>

<script>
import { reactive, toRefs, provide } from "vue";
import Child from "./compoments/Child.vue";
/* 
  provide与inject
  作用：实现祖与后代间通信
  套路：父组件有一个provide选项来提供数据，子组件有一个inject选项来开始使用这些数据
*/
export default {
  components: { Child },
  setup() {
    let car = reactive({ name: "123", price: "456" });
    provide("car", car);
    return {
      ...toRefs(car),
    };
  },
};
</script>

<style>
.app {
  padding: 20px;
  background: rgb(145, 147, 255);
  height: 280px;
  width: 100%;
}
</style>