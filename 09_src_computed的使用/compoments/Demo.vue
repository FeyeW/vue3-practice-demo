<template>
  <input v-model="person.name" /><br />
  <input v-model="person.age" />
  <h2>{{ person.fullName }}</h2>
  <br />
  <input v-model="person.fullName" />
</template>

<script>
import { reactive, computed } from "vue";
export default {
  name: "App",
  components: {},
  setup() {
    let person = reactive({
      name: "张三",
      age: "21",
    });

    //computed的简写使用
    /*     person.fullMsg=computed(()=>{
      return person.name+'-'+person.age
    }) */
    //计算属性——完整写法（考虑读和写）
    person.fullName = computed({
      get() {
        return person.name + "-" + person.age;
      },
      set(value) {
        const nameArr = value.split("-");
        person.name = nameArr[0];
        person.age = nameArr[1];
      },
    });
    return {
      person,
    };
  },
};
</script>

<style>
</style>
