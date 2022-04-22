<template>
  <h2>{{ person.name }}</h2>
  <h2>{{ person.age }}</h2>
  <h2>{{ person.job.salary }}</h2>
  <h2>{{ person.job.a.b.c }}</h2>
  <button @click="test">按钮</button>
</template>

<script>
import Vue from "vue";
//复习vue2响应式原理
/* 
1.实现原理：
  对象类型：通过object.defineProperty()对属性的读取、修改进行拦截（数据劫持）
  数组类型：通过重写更新数组的一系列方法来实现拦截。（对数据的变更方法进行包裹）
2.存在问题
  新增属性、删除属性，界面不会更新
  通过下标直接修改数组，界面不会自动更新
*/
export default {
  name: "App",
  components: {},
  data() {
    return {
      person: {
        name: "123",
        age: "",
        hobby: ["学习", "吃饭"],
      },
    };
  },
  methods: {
    addSex() {
      this.$set(this.person,'sex','女');
      Vue.set(this.person,'sex','女')
    },
    deleteName()
    {
      this.$delete(this.person,'name')
      Vue.delete(this.person,'name','女')
    },
    updateHobby()
    {
      this.$set(this.person.hobby,0,'逛街')
      this.person.hobby.splice(0,1,'逛街')
    }
  },
};
</script>

<style>
</style>
