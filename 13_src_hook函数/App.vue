<template>
  <button @click="handleShow">切换隐藏/显示</button>
  <Demo v-if="isShow"></Demo>
</template>

<script>
import { ref } from "vue";
import Demo from "./compoments/Demo.vue";
export default {
  name: "App",
  components: { Demo },
  /* 自定义hook函数
     什么是hook？————本质是一个函数，把setup函数中使用的Composition API进行了封装
     类似于vue2中的minxin
     自定义hook的优势：复用代码，让setup中的逻辑更清除易懂
   */
  setup() {
    let isShow = ref(true);
    function handleShow() {
      isShow.value = !isShow.value;
    }

    return {
      isShow,
      handleShow,
    };
  },
};
</script>

<style>
</style>
