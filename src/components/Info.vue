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
    padding: 1em 0;
  }
</style>
