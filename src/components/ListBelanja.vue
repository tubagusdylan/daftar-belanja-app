<template>
  <div class="list-container">
    <div class="list-wrapper">
      <div v-for="list in sortedList" :key="list.id" class="list">
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
  import { computed } from "vue";

  const props = defineProps(["listBarang", "editHandler", "sortBy"]);

  const sortedList = computed(() => {
    if (props.sortBy === "check") {
      return props.listBarang.slice().sort((a, b) => a.done - b.done);
    }
    if (props.sortBy === "abjad") {
      return props.listBarang.slice().sort((a, b) => a.nama.localeCompare(b.nama));
    }
    if (props.sortBy === "input") {
      return props.listBarang;
    }
  });

  const listDoneHandler = (list) => {
    list.done = list.done ? false : true;
  };

  const deleteHandler = (list) => {
    const index = props.listBarang.findIndex((current) => {
      return current.id === list.id;
    });

    props.listBarang.splice(index, 1);
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
    vertical-align: middle;
    appearance: none;
    font: inherit;
    margin-right: 10px;
    width: 18px;
    height: 18px;
    border: 3px solid teal;
    border-radius: 5px;
    transform: translateY(-0.075em);
    display: inline-grid;
    place-content: center;
  }

  input.check::before {
    content: "";
    width: 0.65em;
    height: 0.65em;
    transform: scale(0);
    transition: 50ms transform ease-in-out;
    box-shadow: inset 1em 1em teal;
    transform-origin: bottom left;
    clip-path: polygon(14% 44%, 0 65%, 50% 100%, 100% 16%, 80% 0%, 43% 62%);
  }

  input.check:checked::before {
    transform: scale(1);
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
      width: 80%;
    }

    label {
      font-size: large;
    }
  }
</style>
