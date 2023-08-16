<template>
  <div class="input-wrapper">
    <h4>Mari belanja!!!</h4>
    <form>
      <input type="text" placeholder="1" class="jumlah-barang" />
      <input type="text" placeholder="Nama barang" class="nama-barang" />
      <button>Tambah</button>
    </form>
  </div>
</template>

<script setup></script>

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
    width: 50px;
    padding: 5px;
    text-align: center;
  }

  .nama-barang {
    padding: 5px 10px;
  }

  button {
    padding: 5px 10px;
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
