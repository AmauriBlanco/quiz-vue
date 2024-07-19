<script setup>
import { defineProps } from "vue";
import { useRouter } from "vue-router";

const { quiz } = defineProps(["quiz"]);

const router = useRouter();

const navigateToQuiz = () => {
    router.push(`/quiz/${quiz.id}`);
};
</script>
<template>
    <div class="card" @click="navigateToQuiz">
        <img :src="quiz.img" alt="" />
        <div class="card-text">
            <h2>{{ quiz.name }}</h2>
            <p>{{ quiz.questions.length }} questions</p>
        </div>
    </div>
</template>
<style scoped>
/* CARD */
.card {
    border-radius: 2%;
    box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
    cursor: pointer;
    background-color: rgb(43, 43, 43);
}

.card img {
    width: 100%;
    height: auto;
    aspect-ratio: 16/9;
    margin: 0;
    border-radius: 2% 2% 0 0;
}

.card .card-text {
    padding: 1rem;
    font-size: 1.2rem;
    color: #fff;
}

.card .card-text h2 {
    font-weight: bold;
}
</style>
