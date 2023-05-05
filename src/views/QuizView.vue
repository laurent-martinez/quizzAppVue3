<script setup>
import Question from '../components/Question.vue'
import Header from '../components/quiz-header.vue'
import Results from '../components/Results.vue'
import {useRoute} from 'vue-router'
import {ref, computed} from 'vue'
import quizes from '../assets/data/quizes.json'

const route = useRoute()
const showResults = ref(false)
const numberOfCorrectAnswers = ref(0)
const quizId = parseInt(route.params.id)
const quiz = quizes.find(quiz => quiz.id === quizId)
const currentQuestion = ref(0)
const questionStatus = computed(() => `${currentQuestion.value}/${quiz.questions.length}`)
const barPercentage = computed(() => `${(currentQuestion.value / quiz.questions.length) * 100}%`)
const onselectedOption = (isCorrect) => {
    if (isCorrect) {
        numberOfCorrectAnswers.value++
    }
    if (currentQuestion.value === quiz.questions.length - 1) {
        showResults.value = true
    }
    currentQuestion.value++
}
</script>

<template>
    <div>
        <Header :questionStatus="questionStatus"
                :barPercentage="barPercentage"
        />
        <div>
            <Question   v-if="!showResults"
                        :question="quiz.questions[currentQuestion]"
                        @selectOption="onselectedOption"
            />
            <Results 
            :numberOfCorrectAnswers="numberOfCorrectAnswers"
            :quizQuestionsLength="quiz.questions.length"
            v-else />
        </div>
    </div>
</template>

