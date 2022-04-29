<template>
  <h4>{{ person }}</h4>
  <h4>{{ data.x }}</h4>
  <h2>姓名：{{ name }}</h2>
  <h2>年龄：{{ age }}</h2>
  <h2>薪资：{{ salary }}</h2>
  <button @click="name += '~'">修改名字</button>
  <button @click="age += 1">增加年龄</button>
  <button @click="salary++">增加薪水</button>
</template>

<script>
/*
    其他Composition API（不常用）
    一、shallowReactive和shallowRef
    1.原理 
      shallowReactive:只处理对象最外层属性的响应式（浅响应式）
      shallowRef：只处理基本数据类型的响应式，不进行对象的响应式处理
    2.什么时候使用？
      如果有一个对象数据，结构比较深，但变化时只是外层属性变化===>shallowReactive
      如果有一个对象数据，后续功能不会修改该对象的属性，而是生新的对象来替换===>shallowRef
    二、readonly与shallowReadonly
     readonly：让一个响应式数据变为只读（深只读）
     shallowReadonly：让一个响应式数据变为只读（浅只读）
     应用场景：不希望数据被修改时
    三、toRaw与markRaw
      1.toRaw
        作用：将一个由reactive生成的响应式对象转为普通对象
        使用场景：用于读取响应式对象对应的普通对象，对这个普通对象的所有操作，不会引起页面更新
      2.markRaw
        作用：标记一个对象，使其永远不会成为响应式对象
        应用场景：
           有些值不应被设置为响应式的，例如复杂的第三方类库等
           当渲染具有不可变数据源的大列表时，跳过响应式转换可以提高性能
*/
import {
  ref,
  toRef,
  shallowRef,
  shallowReactive,
  readonly,
  shallowReadonly,
  toRaw,
} from "vue";
export default {
  name: "App",
  setup() {
    //只会变化于person里的name值
    let person = shallowReactive({
      name: "张三",
      age: 18,
      job: {
        j1: {
          salary: 20,
        },
      },
    });
    let data = shallowRef({
      x: 0,
    });
    let sum = ref(0);


     function showRawPerson()
     {
       const p=toRaw(person)
       console.log(p)
     }

    person = readonly(person);
    sum = shallowReadonly(sum);
    return {
      showRawPerson,
      person,
      data,
      sum,
      name: toRef(person, "name"),
      age: toRef(person, "age"),
      salary: toRef(person.job.j1, "salary"),
    };
  },
};
</script>

<style>
</style>
