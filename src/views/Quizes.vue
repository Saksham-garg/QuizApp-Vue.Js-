<script>
import q from "../data/quizes.json"
import Card from "../components/Card.vue"
import {
    ref,
    watch
} from "vue"
import gsap from "gsap"
const quizes = ref(q);
const search = ref("")

watch(search, () => {
    quizes.value = q.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
})

const beforeEnter = (el) => {
    console.log(fdas);
    el.style.opacity = 0;
    el.style.transform = "translateY(-100px)"
}
const enter = (el) => {
    gsap.to(el, {
        y: 0,
        opacity: 1,
        duration: 0.4
    })
}
</script>

<template>
<main>
    <header>
        <h1>Quizes</h1>
        <input type="text" placeholder="Search..." v-model.trim="search">
    </header>
    <div class="quiz-container">
        <TransitionGroup appear @before-enter="beforeEnter" @enter="enter">
            <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
        </TransitionGroup>
    </div>
</main>
</template>

<style scoped>
main {
    width: 100vw;
    height: 100vh;
}

header {
    display: flex;
    margin-top: 20px;
    align-items: center;
    margin-bottom: 20px;
}

header h1 {
    margin-right: 30px;

}

header input {
    padding: 7px 7px;
    border: none;
    border-radius: 5px;
}

.quiz-container {
    display: flex;
    flex-wrap: wrap;
    margin-top: 40px;
}
</style>
