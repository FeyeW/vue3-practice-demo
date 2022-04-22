<template>
  <h2>{{ person.name }}</h2>
  <h2>{{ person.age }}</h2>
  <h2>{{ person.job.salary }}</h2>
  <h2>{{ person.job.a.b.c }}</h2>
  <button @click="test">按钮</button>
</template>

<script>
import { reactive } from "vue";
/* 
    Vue3的响应式原理
    1.Proxy代理 （window内置）es6，拦截对象中任意属性的变化
      get 读
      set 修改和追加
      deleteProperty 删除某个属性时调用
    2.Reflect(反射)window内置：对源对象的属性进行操作

*/
export default {
  name: "App",
  components: {},
  setup() {
    let person = reactive({
      name: "张三",
      age: "18",
      job: {
        type: "前端",
        salary: "15k",
        a: {
          b: {
            c: 666,
          },
        },
      },
      hobby: ["123", "学习", "唱歌"],
    });

    function test() {
      person.name = "李四";
      person.job.type = "测试";
      person.job.a.b.c = 7788;
    }

    return {
      person,
      test,
    };
  },
};
</script>

<style>
</style>
