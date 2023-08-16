<template>
  <div class="background">
    <div class="container">
      <Header />
      <Input />
      <ListBelanja />
      <ListControl />
      <Info />
    </div>
  </div>
</template>

<script setup>
  import Header from "./components/Header.vue";
  import Input from "./components/Input.vue";
  import ListBelanja from "./components/ListBelanja.vue";
  import ListControl from "./components/ListControl.vue";
  import Info from "./components/Info.vue";
</script>

<style scoped>
  .background {
    background-color: rgb(122, 166, 169);
  }
  .container {
    width: 100%;
    height: 100vh;
    background-color: teal;
    margin: 0 auto;
  }

  @media (min-width: 768px) {
    .container {
      width: 50%;
      margin: 0 auto;
    }
  }
</style>
