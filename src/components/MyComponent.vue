<template>
  <div class="myCopmonent">My First components on Vue.js</div>
  <h1>{{ msg }}</h1>
</template>

<script>
export default {
  name: "MyComponent",
  props: { msg: String },
};
</script>

<style scoped></style>
