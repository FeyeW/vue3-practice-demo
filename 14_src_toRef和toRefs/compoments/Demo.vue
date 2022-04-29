<template>
  <h4>{{ person }}</h4>
  <h2>姓名：{{ name }}</h2>
  <h2>年龄：{{ age }}</h2>
  <h2>薪资：{{ salary }}</h2>
  <button @click="name += '~'">修改名字</button>
  <button @click="age += 1">增加年龄</button>
  <button @click="salary++">增加薪水</button>
</template>

<script>
/* 
toRef
作用：创建一个ref对象，其value值指向另一个对象中的某个属性
语法：const name=toRef(person,'name')
应用：要将响应式对象中的某个属性单独提供给外部使用时
扩展：toRefs与toRef功能一致，但可以批量创建多个ref对象，语法：toRefs（person）
*/
import { reactive, toRef } from "vue";
export default {
  name: "App",
  setup() {
    let person = reactive({
      name: "张三",
      age: 18,
      job: {
        j1: {
          salary: 20,
        },
      },
    });

    return {
      person,
      name: toRef(person, "name"),
      age: toRef(person, "age"),
      salary: toRef(person.job.j1, "salary"),
      //toRefs不会深层遍历
      /* ...toRefs(person), */
    };
  },
};
</script>

<style>
</style>
