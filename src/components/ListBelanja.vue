<template>
  <div class="list-container">
    <div class="list-wrapper">
      <div v-for="list in listBarang" :key="list.id" class="list">
        <div>
          <input type="checkbox" class="check" :id="list.id" @click="listDoneHandler(list)" :checked="list.done" />
          <label :for="list.id" v-if="list.done" class="list-done">{{ list.total }} {{ list.nama }} </label>
          <label :for="list.id" v-else>{{ list.total }} {{ list.nama }} </label>
        </div>
        <div>
          <button @click="editHandler(list)">Edit</button>
          <button @click="deleteHandler(list)">Hapus</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
  import { ref } from "vue";

  const props = defineProps(["listBarang"]);

  const listDoneHandler = (list) => {
    list.done = list.done ? false : true;
  };

  const deleteHandler = (list) => {
    const index = props.listBarang.findIndex((current) => {
      return current.id === list.id;
    });

    props.listBarang.splice(index, 1);
  };

  const editHandler = (list) => {
    console.log("edit");
  };
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
    display: flex;
    justify-content: space-between;
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

  label {
    font-size: 16px;
  }

  .list-done {
    text-decoration: line-through;
    font-style: italic;
    opacity: 0.5;
  }

  button {
    margin-right: 5px;
    background-color: teal;
    color: white;
    border: none;
    padding: 2px 5px;
    border-radius: 4px;
    cursor: pointer;
  }

  button:hover {
    background-color: rgb(8, 207, 207);
  }

  @media (min-width: 768px) {
    .list-wrapper {
      width: 70%;
    }

    label {
      font-size: large;
    }
  }
</style>
