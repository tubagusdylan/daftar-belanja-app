<template>
  <div class="list-container">
    <div class="list-wrapper"></div>
  </div>
</template>

<script setup></script>

<style scoped>
  .list-container {
    height: 55vh;
    background: whitesmoke;
    border-radius: 10px;
    padding: 10px 0;
    margin: 0 10px;
    overflow-y: auto;
  }

  .list-wrapper {
    width: 100%;
    margin: 5px auto;
    padding: 0 20px;
  }

  @media (min-width: 768px) {
    .list-wrapper {
      width: 70%;
    }
  }
</style>
