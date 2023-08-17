<template>
  <div class="footer">
    <p v-if="listBarang.length > 0">Barang ada {{ listBarang.length }}</p>
    <p v-else>Barang masih kosong!</p>
  </div>
</template>

<script setup>
  const props = defineProps(["listBarang"]);
</script>

<style scoped>
  .footer {
    text-align: center;
    color: white;
    background-color: rgb(1, 71, 71);
    height: 6.9rem;
    padding: 3em 0;
    border-top-left-radius: 20px;
    border-top-right-radius: 20px;
  }
</style>
