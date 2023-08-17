<template>
  <div class="input-wrapper">
    <h4>Mari belanja!!!</h4>
    <div>
      <input type="text" placeholder="1" class="jumlah-barang" :value="total" @input="inputJumlah" />
      <input type="text" placeholder="Nama barang" class="nama-barang" :value="nama" @input="inputBarang" />
      <button v-if="isEdit" @click="onSubmit">Update</button>
      <button v-if="isEdit" @click="cancelEdit">Cancel</button>
      <button v-else @click="onSubmit">Tambah</button>
      <p class="error" v-if="error">Input tidak boleh kosong</p>
    </div>
  </div>
</template>

<script setup>
  const props = defineProps(["total", "nama", "onSubmit", "inputJumlah", "inputBarang", "error", "isEdit", "cancelEdit"]);
</script>

<style scoped>
  .input-wrapper {
    text-align: center;
    margin: 1rem 0;
  }

  h4 {
    color: white;
    margin: 10px 0;
  }

  input {
    display: inline-block;
    margin-right: 10px;
    border: none;
    border-radius: 50px;
  }

  input:focus {
    outline: 3px solid skyblue;
  }

  .error {
    color: rgb(255, 168, 168);
  }

  .jumlah-barang {
    width: 50px;
    padding: 5px;
    text-align: center;
  }

  .nama-barang {
    padding: 5px 10px;
  }

  button {
    padding: 5px 10px;
    margin-right: 5px;
    border: none;
    border-radius: 50px;
    background-color: white;
    color: teal;
  }

  button:hover {
    background-color: rgb(0, 71, 71);
    color: white;
    cursor: pointer;
  }
</style>
