<script setup>
import Questiom from "../components/Question.vue";
import Header from "../components/QuizHeader.vue";
import Result from "../components/Result.vue";
import quizes from "../data/data.json";
import { useRoute } from "vue-router";
import { ref, computed } from "vue";

const route = useRoute();
const quizId = parseInt(route.params.id);

const quiz = quizes.find((q) => q.id === quizId);

const currentQuestionIndex = ref(0);
const numberOfCorrectAnswers = ref(0);

const questionStatus = computed(() => {
    return `${currentQuestionIndex.value}/${quiz.questions.length}`;
});

const barPercentage = computed(
    () => `${(currentQuestionIndex.value / quiz.questions.length) * 100}%`
);

const onOptionSelected = (iscorrect) => {
    if (iscorrect) {
        numberOfCorrectAnswers.value++;
    }

    if (quiz.questions.length - 1 === currentQuestionIndex.value) {
        showResults.value = true;
    }

    currentQuestionIndex.value++;
};

const showResults = ref(false);
</script>

<template>
    <div>
        <Header
            :questionStatus="questionStatus"
            :barPercentage="barPercentage"
        />
        <section>
            <Questiom
                v-if="!showResults"
                @selectOption="onOptionSelected"
                :question="quiz.questions[currentQuestionIndex]"
            />

            <Result
                v-else
                :quizQuestionLength="quiz.questions.length"
                :numberOfCorrectAnswers="numberOfCorrectAnswers"
            />
        </section>
    </div>
</template>
<style scoped>
section {
    margin-top: 20px;
    color: #fff;
}
</style>
