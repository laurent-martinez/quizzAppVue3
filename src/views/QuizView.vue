<script setup>
import Question from '../components/Question.vue'
import Header from '../components/quiz-header.vue'
import {useRoute} from 'vue-router'
import {ref, computed} from 'vue'
import quizes from '../assets/data/quizes.json'

const route = useRoute()
const quizId = parseInt(route.params.id)
const quiz = quizes.find(quiz => quiz.id === quizId)
const currentQuestion = ref(0)
const questionStatus = computed(() => `${currentQuestion.value}/${quiz.questions.length}`)
const barPercentage = computed(() => `${(currentQuestion.value / quiz.questions.length) * 100}%`)
</script>

<template>
    <div>
        <Header :questionStatus="questionStatus"
                :barPercentage="barPercentage"
        />
        <div>
            <Question :question="quiz.questions[currentQuestion]" />
            <button @click="currentQuestion++">Next question</button>
        </div>
    </div>
</template>

