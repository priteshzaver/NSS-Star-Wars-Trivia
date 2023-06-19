<script setup>
const props = defineProps(['eachTriviaData'])
const emit = defineEmits(['flip'])
</script>

<template>
  <div class="card">
    <div class="card-content">
      <div v-if="!props.eachTriviaData.answerShown" class="content">
        {{ props.eachTriviaData.question }}
      </div>
      <div v-else class="content">{{ props.eachTriviaData.answer }}</div>
    </div>
    <footer class="card-footer">
      <button v-if="!props.eachTriviaData.answerShown" @click="emit('flip')">Answer</button>
      <button v-else @click="emit('flip')">Hide</button>
    </footer>
  </div>
</template>

<style scoped></style>
