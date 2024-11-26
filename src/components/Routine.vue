<script setup lang="ts">
import { ref } from 'vue'
import { Button } from 'primevue'

defineProps<{
  title: string
  length: number
}>()
</script>

<template>
  <div
    :style="{
      display: 'block',
      width: '50%',
      borderStyle: 'solid',
      borderColor: 'red',
    }"
  >
    <Button>Create new Routine</Button>
    <div></div>
  </div>
</template>

<style scoped></style>
