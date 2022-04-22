<template>
  <h2>{{ sum }}</h2>
  <button @click="sum++">sum++</button>
  <br />
  <h2>{{ msg }}</h2>
  <button @click="msg += '!'">改变msg</button>
</template>

<script>
import { ref, watch } from "vue";
export default {
  name: "App",
  components: {},
  /* 
    vue2的watch
     watch：{
       简单写法：
       sum(newValue,oldValue) //改变的值 未改变的值
       {
       }
       完整写法：
       sum:{
         immediate:true, 值未变化之前先执行一次
         deep:true  多层级则需要用到deep
         handler(newValue,oldValue)
         {

         }
       }
     }
  */
  setup() {
    let sum = ref(0);
    let msg = ref("你好呀");

    //情况一：监视ref所定义的一个响应式数据
    /*     watch(
      sum,
      (newValue, oldValue) => {
        console.log("new: " + newValue, "old: " + oldValue);
      },
      { immediate: true }
    ); */
    //情况二：监听ref所定义的多个响应式数据
    watch(
      [sum, msg],
      (newValue, oldValue) => {
        console.log("new: " + newValue, "old: " + oldValue);
      },
      { immediate: true }
    );
    return {
      sum,
      msg,
    };
  },
};
</script>

<style>
</style>
