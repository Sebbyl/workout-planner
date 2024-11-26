<script setup lang="ts">
import RoutineSelection from './components/RoutineSelection.vue'
import RoutineList from './components/RoutineList.vue'
import ToggleButton from 'primevue/togglebutton'
import { ref, onUpdated, watch } from 'vue'
import routines from '../routines.json'

const selectedRoutineId = ref()

watch(selectedRoutineId, (newSelectedRoutineId) => {
  console.log(newSelectedRoutineId)
})
</script>

<template>
  <div
    :style="{
      display: 'flex',
      flexDirection: 'row',
      gap: '3rem',
      justifyContent: 'space-between',
      margin: '3rem',
    }"
  >
    <div :style="{ width: '50%' }">
      <RoutineList :routineList="routines" @routineId="(id: number) => (selectedRoutineId = id)" />
    </div>

    <RoutineSelection :routine="routines[selectedRoutineId]" />
  </div>
</template>

<style scoped>
body {
  background-color: white !important;
}
</style>
