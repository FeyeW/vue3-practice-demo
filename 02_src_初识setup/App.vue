<template>
  <h2>{{ name }}</h2>
  <button @click="test">按钮</button>
</template>

<script>
export default {
  name: "App",
  components: {},
 /*  
 1.setup是Composition API的组合 
 2.组件中用到的：数据，方法等均放在setup中
 3.尽量不要和vue2进行混用
 */
  setup() {
    let name = "小明";
    function test() {
      alert(`我被${name}点击了!`);
    }

    return {
      name,
      test,
    };
  },
};
</script>

<style>
</style>
