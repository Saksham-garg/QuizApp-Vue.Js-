<script setup>
    import {defineProps} from "vue"
    const {questionNumber,barPercentage} = defineProps(['questionNumber',"barPercentage"])
</script>

<template>
    <div class="Question-container">
        <header>
            <h3>Question {{questionNumber}}</h3>
            <div class="bar">
                <div class="Question-completion" :style="{width:BarPercentage}"></div>
            </div>
        </header>
    </div>
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
        width: 0%;
        background-color: bisque;
    }
</style>