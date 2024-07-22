<script setup>
import { defineProps } from "vue";

const { questionStatus, barPercentage } = defineProps([
    "questionStatus",
    "barPercentage",
]);
</script>

<template>
    <header>
        <h1>Question {{ questionStatus }}</h1>
        <div class="bar">
            <div class="completion" :style="{ width: barPercentage }"></div>
        </div>
    </header>
</template>
<style scoped>
header {
    padding: 25px 0;
    color: #fff;
    font-size: 2rem;
}

h1 {
    margin-bottom: 20px;
}

.bar {
    width: 300px;
    height: 50px;
    border: solid 3px rgb(77, 86, 211);
    background: rgb(126, 126, 126);
}

.completion {
    height: 100%;
    width: 0%;
    background: rgb(33, 219, 43);
}
</style>
