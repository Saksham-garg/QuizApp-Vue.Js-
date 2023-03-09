<script setup>
    import {defineProps} from 'vue'
    import {RouterLink} from 'vue-router'
    const {numberOfCorrectAnswers,questionsLength} = defineProps(['numberOfCorrectAnswers','questionsLength'])
    
</script>

<template>
    <div class="result">
        <p>Your Results...</p>
        <h1>{{numberOfCorrectAnswers}}/{{ questionsLength }}</h1>
        <RouterLink to="/">Go Back</RouterLink>
    </div>
</template>
<style scoped>
    .result{
        text-align: center;
    }
    .result p{
        font-size: 25px;
    }
    .result h1{
        font-size: 80px;
    }
</style>