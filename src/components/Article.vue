<template>
  <div>
    <h2>Article Component</h2>
    <h2>{{ title }}</h2>
    <h2>Likes - {{ likes }}</h2>
    <h2>Published - {{ isPublished ? "Yes" : "No" }}</h2>
    <ProvideInjectPractice />
  </div>
</template>

<script setup>
import ProvideInjectPractice from "./ProvideInjectPractice.vue";

const props = defineProps({
  title: {
    type: String,
    required: true,
    default: "Article default title",
  },
  likes: Number,
  isPublished: Boolean,
});
</script>

<style scoped></style>
