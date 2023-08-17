<template>
  <div class="input-wrapper">
    <select name="sorting" id="sorting" class="option-sort" :value="sortBy" @change="sortOption">
      <option value="check">Urut berdasarkan checklist</option>
      <option value="input">Urut berdasarkan urutan input</option>
      <option value="abjad">Urut berdasarkan abjad</option>
    </select>
    <button @click="cleanUp">Bersihkan</button>
  </div>
</template>

<script setup>
  const props = defineProps(["cleanUp", "sortBy", "sortOption"]);
</script>

<style scoped>
  .input-wrapper {
    text-align: center;
    margin: 1rem 0;
  }

  .option-sort {
    margin-right: 10px;
    border-radius: 50px;
    padding: 5px;
    border: none;
  }

  .option-sort:focus {
    outline: 3px solid skyblue;
  }

  button {
    padding: 5px 10px;
    border-radius: 50px;
    border: none;
    background-color: white;
    color: teal;
  }

  button:hover {
    background-color: rgb(0, 71, 71);
    color: white;
    cursor: pointer;
  }
</style>
