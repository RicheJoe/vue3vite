<template>
  <div>
    <h1>{{ msg }}</h1>
    <button @click="countFn">count is: {{ count }}</button>
    <attrsDemo v-bind="$attrs"></attrsDemo>
    <button @click="addPerson">++人</button>
    <ul>
      <li v-for="i in userList" :key="i.name">{{ i.name }}:{{ i.age }}</li>
    </ul>
  </div>
</template>

<script>
import { ref, toRefs, onMounted } from 'vue';

import attrsDemo from './attrDemo.vue';
export default {
  name: 'HelloWorld',
  components: {
    attrsDemo,
  },
  inheritAttrs: false,
  props: {
    msg: String, //未使用的attrs传递到下级组件中
  },
  setup(props, context) {
    const { msg } = toRefs(props);
    console.log(props, context.attrs, msg); //注意 setup函数中没有this

    let users = [
      { name: 'zs', age: 10 },
      { name: 'ls', age: 10 },
      { name: 'ww', age: 10 },
    ];

    const count = ref(0);
    const userList = ref(users);

    function countFn() {
      count.value++; //必须用.value 操作数据
    }
    function addPerson() {
      //TODO setup只能操作简单数据   对象格式不可操作
      console.log(typeof userList.value);
    }
    function removePerson() {}
    // mounted
    onMounted(() => {
      console.log('Component is mounted!');
    });
    return {
      count,
      countFn,
      userList,
      addPerson,
    };
  },
};
</script>

<style scoped lang="scss"></style>
