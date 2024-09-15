<template>
  <div>
    <h2>This is a popup</h2>
    <button @click="$emit('close', 1)">Close Popup</button>
    <!-- this second value will be the value passed up to the parent, if needed. can be omitted -->
  </div>
</template>

<script></script>

<style scoped></style>
