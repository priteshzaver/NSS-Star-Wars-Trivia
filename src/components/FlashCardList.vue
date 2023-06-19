<script setup>
import { computed, ref } from 'vue'
import trivia from '../trivia'
import FlashCard from './FlashCard.vue'
import SelectDifficulty from './SelectDifficulty.vue'

const triviaData = ref([...trivia])
const currentDifficulty = ref('all')
const setDifficulty = (difficulty) => {
  currentDifficulty.value = difficulty
}
const filteredTriviaData = computed(() => {
  if (currentDifficulty.value !== 'all') {
    return triviaData.value.filter((each) => each.difficulty === currentDifficulty.value)
  } else return triviaData.value
})

const hideAllAnswers = () => {
  triviaData.value = triviaData.value.map((each) => ({
    ...each,
    answerShown: false
  }))
}
</script>

<template>
  <div>
    <div>
      <SelectDifficulty @difficulty="setDifficulty" />
    </div>
    <button @click="hideAllAnswers">Flip All</button>
    <div class="columns is-multiline mt-5">
      <div v-for="eachTriviaData in filteredTriviaData" :key="eachTriviaData.question">
        <FlashCard
          :eachTriviaData="eachTriviaData"
          @flip="eachTriviaData.answerShown = !eachTriviaData.answerShown"
        />
      </div>
    </div>
  </div>
</template>

<style scoped></style>
