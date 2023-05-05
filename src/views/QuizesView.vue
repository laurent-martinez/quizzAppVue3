<script setup>
import q from '../assets/data/quizes.json'
import { ref, watch } from 'vue'
import QuizCard from '../components/Quiz-card.vue'
const quizes = ref(q)
const search = ref('')
watch(search, (val) => {
  quizes.value = q.filter((quiz) => {
    return quiz.name.toLowerCase().includes(val.toLowerCase())
  })
})
</script>

<template>
  <div>
    <header>
      <h1>Quizes</h1>
      <input  v-model.trim="search" type="text" placeholder="Search...">
    </header>
    <div class="quizes">
      <QuizCard v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
      </div>
    </div>
</template>

<style scoped>

  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
    margin-top: 30px;
  }
  header h1 {
    font-weight: bold;
    margin-right: 30px;
  }
  header input {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 16px;
  }
  .quizes {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin-top: 40px;
  }
  @media screen and (max-width: 800px) {
    header {
      flex-direction: column;
    }
  }
</style>