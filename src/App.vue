<template>
  <div class="container">
    <Header />
    <Input />
  </div>
</template>

<script setup>
  import Header from "./components/Header.vue";
  import Input from "./components/Input.vue";
</script>

<style scoped>
  .container {
    width: 100%;
    height: 100vh;
    background: teal;
    margin: 0 auto;
  }

  @media (min-width: 768px) {
    .container {
      width: 50%;
      margin: 0 auto;
    }
  }
</style>
