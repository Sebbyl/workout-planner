<script setup lang="ts">
import { Button } from 'primevue'
import { ref, watch } from 'vue'

const props = defineProps({
  routine: Object,
})

watch(props, (newRoutine) => {
  console.log(newRoutine.routine)
})
</script>

<template>
  <div
    :style="{
      display: routine ? 'block' : 'none',
      borderStyle: 'solid',
      borderColor: 'red',
      padding: '1rem',
    }"
  >
    <h2>{{ routine?.title }}</h2>
    <div
      v-for="workout in routine?.workouts"
      :style="{ borderColor: 'blue', borderStyle: 'solid', marginBottom: '1rem', padding: '1rem' }"
    >
      <p>Exercise name: {{ workout.name }}</p>
      <p>Rep Range: {{ workout.reps.min }} - {{ workout.reps.max }} reps</p>
      <p>{{ workout.description }}</p>
    </div>
  </div>
</template>

<style scoped></style>
