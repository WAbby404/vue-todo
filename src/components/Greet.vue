<template>
  <h2>Hello {{ name }} a.k.a. {{ heroName }}</h2>
</template>

<script setup>
import { defineProps } from "vue";
const props = defineProps(["name", "heroName"]);

// export default {
//   name: "Greet",
//   props: ["name"],
// };
</script>
