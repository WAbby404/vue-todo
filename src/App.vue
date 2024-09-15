<script setup>
import { ref, watch, reactive, provide } from "vue";
import Greet from "./components/Greet.vue";
import Article from "./components/Article.vue";
import Popup from "./components/Popup.vue";

// Component Events
const showPopup = ref(false);
const closePopup = (value) => {
  showPopup.value = false;
  console.log(value);
};

// Provide & Inject
provide("message", "Taco tuesday!");

const count = ref(0);
provide("count", count);

// Ref practice
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

// Immediate and Deep Watchers
const movie = ref("");

const movieInfo = reactive({ title: "", actor: "" });

// watch(
//   movie,
//   (newMovie, oldMovie) => {
//     console.log(`Calling API with movie name = ${movie.value}`);
//   },
//   { immediate: true }
// );

// watch(
//   movieInfo,
//   (newMovie, oldMovie) => {
//     console.log(
//       `Calling API with movie name 2 = ${movieInfo.title} ${movieInfo.actor}`
//     );
//   },
//   { deep: true }
// );

const movieList = ref(["Batman", "Superman"]);

watch(
  movieList,
  (newMovieList, oldMovieList) => {
    console.log(newMovieList);
  },
  { deep: true }
);

// dont need to do this in reactive components
// export default {
//   name: "App",
//   components: {
//     Greet,
//   },
// };

// Passing reactive props example
const name = ref("Abby");
const channel = ref("Codeevlution");
</script>

<template>
  <!-- Component Events example-->
  <button @click="showPopup = true">Show Popup</button>
  <Popup v-show="showPopup" @close="closePopup" />

  <!-- for provide inject example -->
  <button @click="count += 1">Add 1</button>

  <!-- <Greet name="Toby" heroName="WW" />
  <Greet name="Abby" heroName="Corn" />
  <Greet name="Baby" heroName="BB" />
  <Greet :name="name" :heroName="channel" /> -->

  <Article
    id="my-article"
    title="Article title"
    :likes="9"
    :isPublished="true"
  />
  <!-- 
  <h2>Volume tracker (0 - 20)</h2>
  <h3>Current Volume - {{ volume }}</h3>
  <div>
    <button @click="volume += 2">Increase</button>
    <button @click="volume -= 2">Decrease</button>
  </div>
  <input type="text" v-model="movie" />
  <input type="text" v-model="movieInfo.title" />
  <input type="text" v-model="movieInfo.actor" />
  <button @click="movieList.push('Wonderwoman')">Add Movie</button>
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
  </ul> -->
</template>

<style scoped></style>
