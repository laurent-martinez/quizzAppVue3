<script setup>
const props = defineProps(['question'])
</script>

<template>
    <div>
        <div class="question-container">
            <h1 class="question">{{props.question.text}} ?</h1>
        </div>
        <div class="options-container">
            <div v-for="option in props.question.options" :key="option.id" class="option">
                <p class="option-label">{{option.label}}</p>
                <div class="option-value">
                    <p>{{option.text}}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>

    .question-container {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 200px;
    }
    .question {
        margin: 0;
        font-size: 1.5rem;
        font-weight: 400;
    }
    .options-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 200px;
    }
    .option {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 300px;
        height: 50px;
        background-color: #FFC69E;
        border-radius: 5px;
        margin-bottom: 10px;
    }
    .option-label {
        margin: 0 auto;
        padding: 20px;
        font-size: 1.5rem;
        font-weight: 400;
    }
    .option-value {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
        height: 100%;
        background-color: #C9C6E4;
        border-radius: 0 5px 5px 0;
    }
    .option-value p {
        margin: 0;
        font-size: 1.5rem;
        font-weight: 400;
    }
</style>