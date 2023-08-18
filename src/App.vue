<template>
  <div class="background">
    <div class="container">
      <Header />
      <Input :total="totalBarang" :nama="namaBarang" :onSubmit="addList" :inputJumlah="inputJumlah" :inputBarang="inputBarang" :errorNama="errorNama" :errorJumlah="errorJumlah" :isEdit="isEdit" :cancelEdit="cancelEditHandler" />
      <ListBelanja :listBarang="listBarang" :editHandler="editHandler" :sortBy="sortBy" />
      <ListControl :cleanUp="cleanUp" :sortBy="sortBy" :sortOption="sortOptionHandle" />
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
  const errorJumlah = ref(false);
  const errorNama = ref(false);
  const idList = ref(1);
  const isEdit = ref(false);
  const editList = ref({});
  const sortBy = ref("check");

  const inputJumlah = (e) => {
    totalBarang.value = e.target.value;
  };
  const inputBarang = (e) => {
    namaBarang.value = e.target.value;
  };

  const sortOptionHandle = (e) => {
    sortBy.value = e.target.value;
  };

  const addList = () => {
    if (namaBarang.value.length === 0) {
      errorNama.value = true;
      return;
    }

    if (totalBarang.value.length === 0) {
      errorJumlah.value = true;
      return;
    }

    // For edit list
    if (editList.value.id) {
      const updateList = {
        id: editList.value.id,
        total: totalBarang.value,
        nama: namaBarang.value,
        done: false,
      };

      const index = listBarang.value.findIndex((current) => {
        return current.id === editList.value.id;
      });

      listBarang.value.splice(index, 1, updateList);

      errorNama.value = false;
      errorJumlah.value = false;

      return cancelEditHandler();
    }

    listBarang.value.push({ id: idList.value, total: totalBarang.value, nama: namaBarang.value, done: false });
    totalBarang.value = "";
    namaBarang.value = "";
    idList.value++;
    errorNama.value = false;
    errorJumlah.value = false;
  };

  const editHandler = (list) => {
    editList.value = list;
    totalBarang.value = list.total;
    namaBarang.value = list.nama;
    isEdit.value = true;
  };

  const cancelEditHandler = () => {
    isEdit.value = false;
    totalBarang.value = "";
    namaBarang.value = "";
    editList.value = {};
  };

  const cleanUp = () => {
    listBarang.value = [];
  };
</script>

<style scoped>
  .background {
    background-color: rgb(122, 166, 169);
  }
  .container {
    width: 100%;
    min-height: 100vh;
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
