<script setup>
import {RouterLink} from 'vue-router'
const props = defineProps(['numberOfCorrectAnswers', 'quizQuestionsLength'])
const success = props.numberOfCorrectAnswers > props.quizQuestionsLength / 2
console.log(success);
</script>

<template>
    <div class="results">
        <p>Your results</p>
        <h1 :class="success ? 'greenTextClass': 'redTextClass'">{{props.numberOfCorrectAnswers}}/{{props.quizQuestionsLength}}</h1>
        <RouterLink to="/" class="button">Play again</RouterLink>
    </div>
</template>

<style scoped>
    .results {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        margin-top: 50px;
    }
    p {
        margin: 0;
        font-size: 1.5rem;
        font-weight: 400;
    }
    h1 {
        margin: 0;
        font-size: 3rem;
        font-weight: 400;
    }
    .button {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 300px;
        height: 50px;
        background-color: #FFC69E;
        border-radius: 5px;
        margin-top: 50px;
        text-decoration: none;
        color: #000;
        font-size: 1.5rem;
        font-weight: 400;
    }
    .button:hover {
        cursor: pointer;
        opacity: 0.7;
    }
    .greenTextClass {
        color: #00FF00;
    }
    .redTextClass {
        color: #FF0000;
    }
</style>