<script setup>
const emit = defineEmits(['difficulty'])

const selectedDifficulty = (difficulty) => {
  emit('difficulty', difficulty)
}
</script>

<template>
  <button @click="selectedDifficulty('easy')">Easy</button>
  <button @click="selectedDifficulty('medium')">Medium</button>
  <button @click="selectedDifficulty('hard')">Hard</button>
  <button @click="selectedDifficulty('all')">All</button>
</template>

<style scoped></style>
