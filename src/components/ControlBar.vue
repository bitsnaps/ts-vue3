<script setup lang="ts">
import { ref, onMounted } from 'vue'

// defineEmits is another Compile Macro
const emit = defineEmits<{
  // Define a call signature
  (event: 'add-count', number: number): void
  // 'reset-event' is a Literal Type and not string
  (event: 'reset-count'): void
}>()

</script>

<template>
  <div>
    <button type="button" @click="emit('add-count', 1)">Add</button>
    <button type="button" @click="emit('reset-count')">Reset</button>
  </div>
</template>

<style scoped>
</style>
