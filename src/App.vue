<template>
  <div class="background">
    <div class="container">
      <Header />
      <Input :total="totalBarang" :nama="namaBarang" :onSubmit="addList" :inputJumlah="inputJumlah" :inputBarang="inputBarang" :error="errorInput" />
      <ListBelanja :listBarang="listBarang" />
      <ListControl />
      <Info :listBarang="listBarang" />
    </div>
  </div>
</template>

<script setup>
  import Header from "./components/Header.vue";
  import Input from "./components/Input.vue";
  import ListBelanja from "./components/ListBelanja.vue";
  import ListControl from "./components/ListControl.vue";
  import Info from "./components/Info.vue";
  import { ref } from "vue";

  const listBarang = ref([]);
  const totalBarang = ref("");
  const namaBarang = ref("");
  const errorInput = ref(false);
  const idList = ref(1);

  const inputJumlah = (e) => {
    totalBarang.value = e.target.value;
  };
  const inputBarang = (e) => {
    namaBarang.value = e.target.value;
  };

  const addList = () => {
    if (namaBarang.value.length === 0 || totalBarang.value.length === 0) {
      errorInput.value = true;
      return;
    }
    listBarang.value.push({ id: idList.value, total: totalBarang.value, nama: namaBarang.value, done: false });
    totalBarang.value = "";
    namaBarang.value = "";
    idList.value++;
    errorInput.value = false;
  };
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
