<script setup>
    import {defineProps} from "vue";
    import { useRoute } from "vue-router";
    const {quiz} = defineProps(['quiz'])

    const router = useRoute();  
    const quizID = parseInt(router.params.id);
    const navigateQuiz = () =>{
        router.push(`http://localhost:5173/quiz/${quizID}`)
    }

</script>

<template>
    <div class="card" @click="navigateQuiz()">
        <img :src="quiz.img" alt="Pic">
        <div class="card-text">
          <h3>{{quiz.name}}</h3>
          <p>{{quiz.questions.length}} Questions</p>
        </div>
      </div>
</template>

<style scoped>
      .card{
    width: 225px;
    height: 225px;
    overflow: hidden;
    margin-right: 20px;
    border-radius: 5px;
  }
  .card img{
    width: 100%;
    height: 165px;
  }
</style>