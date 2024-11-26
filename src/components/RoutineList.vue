<script setup lang="ts">
import { ref, watch } from 'vue'
import { Button, ToggleButton } from 'primevue'

defineProps<{
  routineList: any[]
}>()

// const routines = ref([
//   {
//     id: 0,
//     title: 'Testing Routine',
//     length: 2,
//     description: '',
//     workouts: [
//       { workoutId: 0, name: 'Barbell Bench Press', reps: { min: 4, max: 8 }, description: '' },
//       { workoutId: 1, name: 'Dumbbell Lateral Raise', reps: { min: 8, max: 12 }, description: '' },
//       { workoutId: 2, name: 'Tricep Extension', reps: { min: 8, max: 12 }, description: '' },
//       {
//         workoutId: 3,
//         name: 'Incline Dumbbell Bench Press',
//         reps: { min: 8, max: 12 },
//         description: '',
//       },
//     ],
//   },
//   { id: 1, title: 'Testing Routine 2', length: 6 },
// ])

const emit = defineEmits(['routineId'])

const checkedButton = ref()

watch(checkedButton, (newCheckedButton) => {
  console.log(newCheckedButton)
})

const handleRoutineSelection = (id: number) => {
  checkedButton.value = id
  emit('routineId', id)
}
</script>

<template>
  <div
    :style="{
      display: 'flex',
      flexDirection: 'column',
      borderStyle: 'solid',
      borderColor: 'red',
      gap: '2rem',
      padding: '1rem',
      flexWrap: 'wrap',
    }"
  >
    <div :style="{ display: 'flex', flexDirection: 'row', gap: '2rem' }">
      <div v-for="routine in routineList">
        <ToggleButton
          @click="handleRoutineSelection(routine.id)"
          :active="checkedButton === routine.id"
          :style="{
            display: 'block',
            borderStyle: 'solid',
            borderColor: 'blue',
            padding: '1rem',
            width: 'auto',
            backgroundColor: checkedButton === routine.id ? 'red' : 'white',
          }"
        >
          <div>
            <h3>
              {{ routine.title }}
            </h3>

            <p>Routine length: {{ routine.workouts.length }} days</p>
          </div>
        </ToggleButton>
      </div>
    </div>

    <div :style="{ display: 'flex' }">
      <Button>Create new Routine</Button>
    </div>
  </div>
</template>

<style scoped></style>
