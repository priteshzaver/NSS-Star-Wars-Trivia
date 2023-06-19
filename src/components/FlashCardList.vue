<script setup>
import { ref } from 'vue'
import trivia from '../trivia'
import FlashCard from './FlashCard.vue'

const triviaData = ref([...trivia])
</script>

<template>
  <div class="columns is-multiline">
    <div v-for="eachTriviaData in triviaData" :key="eachTriviaData.question">
      <FlashCard
        :eachTriviaData="eachTriviaData"
        @flip="eachTriviaData.answerShown = !eachTriviaData.answerShown"
      />
    </div>
  </div>
</template>

<style scoped></style>
