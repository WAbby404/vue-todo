<script setup>
import { ref, watch } from "vue";

const list = ref(["Task 1"]);
const currentTask = ref("");

const deleteTask = (index) => {
  list.value.splice(index, 1);
};

const addTask = () => {
  list.value.push(`${currentTask.value}`);
  currentTask.value = "";
};

const editTask = (task, index) => {
  currentTask.value = task;
  deleteTask(index);
};

// Watcher example
const volume = ref(0);

watch(volume, (newVolume, oldVolume) => {
  console.log(volume.value);
  console.log(newVolume);
  console.log(oldVolume);
  if (newVolume > oldVolume && newVolume === 16) {
    alert("This may cause harm.");
  }
});
</script>

<template>
  <h2>Volume tracker (0 - 20)</h2>
  <h3>Current Volume - {{ volume }}</h3>
  <div>
    <button @click="volume += 2">Increase</button>
    <button @click="volume -= 2">Decrease</button>
  </div>
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
      <button @click="deleteTask(index)">X</button>
    </li>
  </ul>
</template>

<style scoped></style>
