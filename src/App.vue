<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <HelloWorld dataTable="datalist" msg="vite " v2="grandPa" />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
  data() {
    return {
      datalist: 'xxx',
    };
  },
  inheritAttrs: false,
};
</script>
