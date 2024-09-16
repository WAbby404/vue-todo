<template>
  <button @click="notifyParent">Notify Parent</button>
</template>

<script setup>
import { defineEmits } from "vue";

const emit = defineEmits(["customEvent"]);
function notifyParent() {
  emit("customEvent", { message: "Hello from child." });
}
</script>

<style scoped></style>
