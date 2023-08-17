<template>
  <div class="list-container">
    <div class="list-wrapper">
      <div v-for="list in listBarang" :key="list.id" class="list">
        <input type="checkbox" class="check" />
        <span>{{ list.total }} {{ list.nama }}</span>
      </div>
    </div>
  </div>
</template>

<script setup>
  const props = defineProps(["listBarang"]);
</script>

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

  .list {
    border-bottom: 1px solid grey;
    padding: 7px 10px;
  }

  .list:last-child {
    border-bottom: none;
  }

  input.check {
    display: inline-block;
    vertical-align: middle;
    cursor: pointer;
    width: 18px;
    height: 18px;
    margin-right: 10px;
  }

  span {
    font-size: 16px;
  }

  @media (min-width: 768px) {
    .list-wrapper {
      width: 70%;
    }

    span {
      font-size: large;
    }
  }
</style>
