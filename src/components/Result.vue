<script setup>
import { defineProps } from "vue";
import { RouterLink } from "vue-router";

const { quizQuestionLength, numberOfCorrectAnswers } = defineProps([
    "quizQuestionLength",
    "numberOfCorrectAnswers",
]);
</script>

<template>
    <div class="results">
        <p>Your Results...</p>
        <p class="result">
            {{ numberOfCorrectAnswers }}/{{ quizQuestionLength }}
        </p>
        <RouterLink class="link" to="/">Go Back</RouterLink>
    </div>
</template>
<style scoped>
.results {
    text-align: center;
    padding: 100px 0;
}

p {
    font-size: 3rem;
}

.result {
    font-size: 4rem;
}

.link {
    padding: 10px 25px;
    font-size: 2rem;
    background: rgb(22, 105, 73);
    color: #fff;
    transition: 0.6s;
    border-radius: 5px;
    box-shadow:3px 4px 5px 2px rgba(22, 105, 73, 0.315);
}
</style>
