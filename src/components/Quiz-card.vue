<script setup>
import {useRouter} from 'vue-router'
const router = useRouter();
const props = defineProps(['quiz']);
const navigateToQuiz = () => {
    router.push(`/quiz/${props.quiz.id}`)
}
</script>

<template>
    <div  class="card" @click="navigateToQuiz">
        <img :src="quiz.img" alt="Quiz 1">
        <div class="card-text">
          <h2>{{quiz.name}}</h2>
          <p>{{quiz.questions.length}} questions</p>
        </div>
    </div>
</template>

<style scoped>
.card {
    width: 310px;
    overflow: hidden;
    border-radius: 2%;
    box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
    margin-bottom: 35px;
    margin-right: 20px;
    cursor: pointer;
  }
.card:hover {
    box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.2);
    opacity: 0.5;
  }
  .card img {
    width: 100%;
    height: 200px;
    object-fit: cover;
    margin: 0;
  }

  .card .card-text {
    padding: 0 10px;
  }
  .card .card-text h2 {
    font-size: 20px;
    font-weight: bold;
    margin: 0;
    margin-bottom: 10px;
  }
</style>