<script setup>
import { defineProps } from "vue";

const { quiz } = defineProps(["quiz"]);
</script>
<template>
    <div class="card">
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
}

.card .card-text h2 {
    font-weight: bold;
}
</style>
