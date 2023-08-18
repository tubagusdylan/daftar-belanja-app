<template>
  <div class="input-wrapper">
    <h4>Mari belanja!!!</h4>

    <div>
      <input type="number" placeholder="1" class="jumlah-barang" :class="[errorNama ? 'error-style' : 'correct-style']" :value="total" @input="inputJumlah" />
      <input type="text" placeholder="Nama barang" class="nama-barang" :class="[errorNama ? 'error-style' : 'correct-style', isEdit ? 'edit-style' : 'non-edit-style']" :value="nama" @input="inputBarang" />
      <button v-if="isEdit" @click="onSubmit">Update</button>
      <button v-if="isEdit" @click="cancelEdit">Cancel</button>
      <button v-else @click="onSubmit">Tambah</button>
    </div>
  </div>
</template>

<script setup>
  const props = defineProps(["total", "nama", "onSubmit", "inputJumlah", "inputBarang", "errorNama", "errorJumlah", "isEdit", "cancelEdit"]);
</script>

<style scoped>
  .input-wrapper {
    text-align: center;
    margin: 2rem 0;
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

  .jumlah-barang {
    width: 60px;
    padding: 5px;
    text-align: center;
  }

  .nama-barang {
    padding: 5px 10px;
  }

  .edit-style {
    display: block;
    margin: 10px auto;
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

  .error-style {
    outline: 3px solid rgb(255, 100, 100);
  }

  .correct-style {
    outline: none;
  }

  @media (min-width: 768px) {
    .nama-barang {
      display: inline-block;
    }

    .edit-style {
      display: inline-block;
      margin: 0 10px;
    }
  }
</style>
