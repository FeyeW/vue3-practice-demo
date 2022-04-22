<template>
  <h2>{{ name }}</h2>
  <h2>{{ job.salary }}</h2>
  <button @click="test">按钮</button>
</template>

<script>
//setup中引用ref作为响应式数据的引用对象 作用:定义一个响应式的数据
import { ref } from "vue";
export default {
  name: "App",
  components: {},
  /*  
 1.接收的数据可以是基本类型，也可以是对象类型
 */
  setup() {
    let name = ref("小明");
    let job = ref({
      name: "工程师",
      salary: "10k",
    });
    function test() {
      //alert(`我被${name}点击了!`);
      name.value = "大明";
      job.value.name = "设计师";
      job.value.salary = "20k";
    }

    return {
      name,
      job,
      test,
    };
  },
};
</script>

<style>
</style>
