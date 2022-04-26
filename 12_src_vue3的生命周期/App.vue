<template>
  <button @click="handleShow">切换隐藏/显示</button>
  <Demo v-if="isShow"></Demo>
</template>

<script>
import {
  ref,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from "vue";
import Demo from "./compoments/Demo.vue";
export default {
  name: "App",
  components: { Demo },
  /* setup相当于created */
  setup() {
    let isShow = ref(true);
    function handleShow() {
      isShow.value = !isShow.value;
    }

    onBeforeMount(() => {});
    onMounted(() => {});
    onBeforeUpdate(() => {});
    onUpdated(() => {});
    onBeforeUnmount(() => {});
    onUnmounted(() => {});

    return {
      isShow,
      handleShow,
    };
  },
};
</script>

<style>
</style>
