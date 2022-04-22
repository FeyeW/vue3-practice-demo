<template>
  <h2>{{ person.msg }}</h2>
  <h2>{{ person.school }}</h2>
  <button @click="handle">按钮</button>
</template>

<script>
export default {
  name: "App",
  components: {},
  props: ["msg", "school"],
  emits: ["hello"],
  setup(props, context) {
    //props的使用
    console.log(props);
    let person = {
      msg: props.msg,
      school: props.school,
    };
    //context中emit的使用
    console.log(context);
    function handle() {
      context.emit("hello", 666);
    }
    //context中slot的使用
    console.log(context.slots);

    return {
      person,
      handle,
    };
  },
};
</script>

<style>
</style>
