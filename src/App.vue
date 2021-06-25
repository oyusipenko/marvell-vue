<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
  <MyComponent msg="test porps" />
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import MyComponent from "./components/MyComponent.vue";

export default {
  name: "App",
  components: {
    // HelloWorld,
    MyComponent,
  },
};
</script>

<style></style>
