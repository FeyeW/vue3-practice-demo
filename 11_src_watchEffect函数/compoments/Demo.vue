<template>
  <h2>{{ sum }}</h2>
  <button @click="sum++">sum++</button>
  <br />
  <h2>{{ msg }}</h2>
  <button @click="msg += '!'">改变msg</button>
</template>

<script>
/* 
   1.watch的套路是：既要指明监视的属性，也要指明监视的回调
   2.watchEffect的套路是:不用指明监视哪个属性，监视的回调中用到哪个属性，那就监视那个属性
   3.watchEffect有点像computed：
       但computed注重的是计算出来的值（回调函数的返回值），所以必须要写返回值
       而WatchEffect更注重的是过程（回调函数的函数体），所以不用写返回值
*/
import { reactive, watchEffect } from "vue";
export default {
  name: "App",
  components: {},
 
  setup() {
    let person=reactive({
      name:'张三',
      age:18,
      job:{
        j1:{
          salary:20
        }
      }
    })
     watchEffect(()=>{
        const x1=sum.value
        const x2=person.job.j1.salary
        console.log('变化了')
     })
    return {
      person
    };
  },
};
</script>

<style>
</style>
