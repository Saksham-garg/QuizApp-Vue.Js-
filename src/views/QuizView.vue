<script setup>
    import Question from "../components/Question.vue"
    import QuestionBar from "../components/QuestionBar.vue"
    import {ref,watch,computed} from "vue"
    import quiz from "../data/quizes.json"
    import { useRoute } from "vue-router"
    import Results from '../views/Results.vue'

    const route = useRoute(); 
    const quizId = parseInt(route.params.id);

    const q = quiz.find(q => q.id === quizId)
    const QuestionNumberIndex = ref(0);

    const QuestionNumber = ref(`${QuestionNumberIndex.value}/${q.questions.length}`)
    const BarPercentage = computed(()=>`${QuestionNumberIndex.value/q.questions.length *100}%`)
    const numberOfCorrectAnswers = ref(0)
    watch(()=>QuestionNumberIndex.value,()=>{
        QuestionNumber.value = `${QuestionNumberIndex.value}/${q.questions.length}`;
    })

    const onOptionSelected = (isCorrect) =>{
        if(isCorrect){
            numberOfCorrectAnswers.value++;
        }

        if(q.questions.length - 1 === QuestionNumberIndex.value){
            showResults.value = true;
        }
        QuestionNumberIndex.value++;
    }

    const showResults = ref(false);
</script>
<template>
    {{ BarPercentage }}
    <QuestionBar :questionNumber="QuestionNumber" :barPercentage = "BarPercentage"></QuestionBar>
    <Question v-if="!showResults" :question="q.questions[QuestionNumberIndex]" @selectOption="onOptionSelected"></Question>
    <Results v-else :numberOfCorrectAnswers="numberOfCorrectAnswers" :questionsLength="q.questions.length"></Results>
</template>

<style scoped>
    header{
        margin-top: 20px;
    }

    header h3{
        font-size: 20px;
    }
    .bar{
        width: 300px;
        height: 50px;
        border-color: bisque;
        border: 2px solid red;
    }
    .Question-completion{
        height: 100%;
        width: 33%;
        background-color: bisque;
    }

    .Question-container{
        margin-top: 20px;
    }
    .Question p{
        font-size: 30px;
    }

    .option{
        display: flex;
    }
    .option-label{
        height: 50px;
        width: 50px;
        background-color: bisque;
        font-size: 30px;
        display: flex;
        align-items: center;
        justify-content: center;
        color: black;
        
    }
    .option-value{
        background-color: rgb(244,239,239);
        width: 100%;
        font-size: 30px;
        padding: 0px 10px;
        color: black;   
    }
</style>