<template>
  <button @click="notifyParent">Notify Parent</button>
</template>

<script setup>
const emit = defineEmits(["customEvent"]);
function notifyParent() {
  emit("customEvent", { message: "Hello from child." });
}
</script>

<style scoped></style>
