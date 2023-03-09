<script setup>
    import quiz from "../data/quizes.json"
    import {defineProps,defineEmits} from "vue"
    const {question} = defineProps(['question'])
    
    const emit = defineEmits(['selectOption'])
    const emitSelectedOption = (isCorrect) =>{
        emit('selectOption',isCorrect)
    }
</script>
<template>
    <div class="Question-container" >
        <div class="Question">
            <p>{{question.text}}</p>
        </div>
        <div v-for="option in question.options" class="options-container"
         :key="option.id" @click="emitSelectedOption(option.isCorrect)">
            <div class="option">
                <p class="option-label">{{option.label}}</p>
                <div class="option-value">
                    <p>{{option.text}}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
   

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