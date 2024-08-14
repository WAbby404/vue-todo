<script setup>
import { ref } from "vue";

const list = ref(["Task 1"]);
const currentTask = ref("");

const deleteTask = (index) => {
  list.value.splice(index, 1);
};

const addTask = () => {
  console.log(currentTask.value);
  list.value.push(`${currentTask.value}`);
  currentTask.value = "";
};

const editTask = (task, index) => {
  currentTask.value = task;
  deleteTask(index);
};
</script>

<template>
  <h1>Vue todo list</h1>
  <form @submit.prevent="addTask">
    <label for="task">Add Task</label>
    <input type="text" id="task" name="task" v-model="currentTask" />
    <button type="submit">Submit</button>
  </form>
  <ul>
    <li v-for="(task, index) in list" :key="index">
      <h2>{{ task }}</h2>
      <button @click="editTask(task, index)">Edit</button>
      <button @click="deleteTask(task, index)">X</button>
    </li>
  </ul>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
