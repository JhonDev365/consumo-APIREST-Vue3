<script setup>
import { ref } from 'vue';

const counter = ref(0);
const increment = () => {
  counter.value++;
};
</script>

<template>
  <button @click="increment" class="btn btn-success mb-3">
    Press Counter {{ counter }}
  </button>
</template>

<style scoped></style>
