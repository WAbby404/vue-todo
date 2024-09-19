<template>
  <input type="text" v-model="model" />
</template>

<script setup>
const model = defineModel();
</script>

<style scoped>
input[type="text"] {
  background-color: #95f8ff;
  border: 1px solid red;
}
</style>
