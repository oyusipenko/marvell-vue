<template>
  <div class="demo-container">
    <NavBar />
    <Drawer />
    <MainContent />
  </div>
</template>

<script>
import NavBar from "./components/NavBar.vue";
import Drawer from "./components/Drawer.vue";
import MainContent from "./components/MainContent.vue";

export default {
  name: "App",
  components: {
    NavBar,
    Drawer,
    MainContent,
  },
};
</script>

<style>
body {
  margin: 0;
}
</style>
