<template>
  <h2>{{ person.name }}</h2>
  <h2>{{ person.age }}</h2>
  <h2>{{ person.job.salary }}</h2>
  <h2>{{ person.job.a.b.c }}</h2>
  <button @click="test">按钮</button>
</template>

<script>
//setup中引用reactive对象类型的响应式数据（基本类型用ref函数）
//reactive定义的响应式数据是“深层次的”
//内部基于ES6的Proxy实现，通过代理对象操作源对象内部数据进行操作
import { reactive } from "vue";
export default {
  name: "App",
  components: {},
  /*  
 1.接收的数据可以是基本类型，也可以是对象类型
 */
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
