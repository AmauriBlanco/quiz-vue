<script setup>
import { defineProps, defineEmits } from "vue";
const { question } = defineProps(["question"]);

const emit = defineEmits(["selectOption"]);

const emitSelectedOption = (isCorrect) => {
    emit('selectOption', isCorrect)
};
</script>
<template>
    <div class="question-container">
        <h2 class="question">{{ question.text }}</h2>
    </div>
    <div class="options-container">
        <div
            v-for="option in question.options"
            :key="option.id"
            @click="emitSelectedOption(option.isCorrect)"
            class="option"
        >
            <p class="option-label">{{ option.label }}</p>
            <div class="option-value">
                <p>{{ option.text }}</p>
            </div>
        </div>
    </div>
</template>
<style scoped>
.question {
    font-size: 3rem;
    margin-block: 20px;
}

.options-container {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

.option {
    display: flex;
    align-items: center;
    font-size: 2rem;
    color: #fff;
    cursor: pointer;
    transition: 0.6s;
}

.option:hover {
    transform: scale(1.05);
}

.option-label {
    display: grid;
    place-items: center;
    width: 60px;
    height: 60px;
    font-size: 2.2rem;
    color: #fff;
    text-transform: uppercase;
    transition: 0.6s;
    background: rgb(54, 58, 120);
}

.option-value {
    height: 60px;
    width: 100%;
    padding: 0 1rem;
    display: flex;
    align-items: center;
    transition: 0.6s;
    background: rgba(54, 58, 120, 0.534);
}
</style>
