<template>
  <h2>{{ sum }}</h2>
  <button @click="sum++">sum++</button>
  <br />
  <h2>{{ msg }}</h2>
  <button @click="msg += '!'">改变msg</button>
</template>

<script>
import { ref, watch,reactive } from "vue";
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
    let person=reactive({
      name:'张三',
      age:'18',
      job:{
        j1:{
          salary:20
        }
      }
    })
    //情况一：监视ref所定义的一个响应式数据
    /*     watch(
      sum,
      (newValue, oldValue) => {
        console.log("new: " + newValue, "old: " + oldValue);
      },
      { immediate: true }
    ); */
    //情况二：监听ref所定义的多个响应式数据
    /*     watch(
      [sum, msg],
      (newValue, oldValue) => {
        console.log("new: " + newValue, "old: " + oldValue);
      },
      { immediate: true }
    ); */
    /* 
    情况三：监听reactive所定义的一个响应式数据的全部属性
        1.注意：此处无法正确获取oldValue
        2.注意:强制开启了深度监视（deep配置无效）
        watch(person,(newValue,oldValue)=>{
          console.log('person的name变化了',newValue,oldValue)
        },{deep:false}) 此处的deep配置无效
     */
    /* 
    情况四：监听reactive所定义的一个响应式数据中的某个属性
    watch(()=>person.name,(newValue,oldValue)=>{
      console.log('person的name变化了',newValue,oldValue)
    })
    */
   /* 
   情况五：监听reactive所定义的一个响应式数据中的某些属性
   watch([()=>person.name,()=>person.age],(newValue,oldValue)=>{
     console.log('person的name或age变化了',newValue,oldValue)
   })
    */
   /* 
   特殊情况：
   watch(()=>person.job,(newValue,oldValue)=>{
     console.log('....',newValue,oldValue)
   },{deep:true})  //当监视的是reactive定义对象的某个属性 也就是对象的对象的时候，deep配置有效
   */
    return {
      sum,
      msg,
    };
  },
};
</script>

<style>
</style>
