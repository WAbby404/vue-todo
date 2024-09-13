<template>
  <h2>Hello World</h2>
  <h3>{{ message }}</h3>
  <h3>{{ count }}</h3>
</template>

<script setup>
import { inject } from "vue";

const message = inject("message");
const count = inject("count");
</script>

<style scoped></style>
