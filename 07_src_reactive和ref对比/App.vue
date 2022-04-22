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
    reactive对比ref
    1.从定义数据角度对比：
      ref用来定义：基本数据类型
      reactive用来定义：对象（或数组）类型数据
      备注：ref也可以用来定义对象（或数组）类型数据，它内部会自动通过reactive转为代理对象
    2.从原理角度对比：
      ref通过Object.defineProperty()的get和set来实现响应式（数据劫持）
      reactive通过使用Proxy来实现响应式（数据劫持），并通过Reflect操作源对象内部的数据
    3.从使用角度对比：
      ref定义的数据：操作数据需要.value，读取数据时模板中直接读取不需要.value
      reactive定义的数据：操作数据和读取数据：均不需要.value
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
