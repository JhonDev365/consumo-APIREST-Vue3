<template>
  <div>
    <button
      @click="emit('previus')"
      class="btn btn-outline-primary"
      :disabled="inicio === 0"
    >
      Previus {{ inicio }}
    </button>
    <button
      @click="emit('next')"
      class="btn btn-outline-primary"
      :disabled="fin === max"
    >
      Next {{ fin }}
    </button>
  </div>
</template>

<script setup>
const props = defineProps(['inicio', 'fin', 'max']);
const emit = defineEmits(['next', 'previus']);
</script>
