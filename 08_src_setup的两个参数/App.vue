<template>
  <Demo @hello="sayHello" msg="你好啊" school="123">
    <template v-slot:qwe>
      <span>7788</span>
    </template>
  </Demo>
</template>

<script>
/* 
   setup的两个注意点
    1.setup执行的时机
      在beforeCreate之前执行一次，this是undefined
    2.setup的参数
      props：值为对象，包含：组件外部传递过来，且组件内部声明接收了的属性
      context：上下文对象
        attrs：值为对象，包含：组件外部传递过来，但没有在props配置中声明的属性，相当于this.$attrs
        slots:收到的插槽内容，相当于this.$slots
        emit:分发自定义事件的函数，相当于this.$emit
*/
import Demo from "./compoments/Demo.vue";
export default {
  name: "App",
  components: { Demo },
  setup() {
    function sayHello(value) {
      alert(`我收到${value}`);
    }
    return {
      sayHello,
    };
  },
};
</script>

<style>
</style>
