<template>
  <div>
    <h2>This is a popup</h2>
    <input type="text" v-model="name" />
    <button @click="$emit('close', name)">Close Popup</button>
    <!-- this second value will be the value passed up to the parent, if needed. can be omitted -->
  </div>
</template>

<script>
import { ref } from "vue";

const name = ref("");
</script>

<style scoped></style>
