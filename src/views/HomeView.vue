<script setup>
import q from "../data/data.json";
import { ref, watch } from "vue";
import Card from "../components/Card.vue";
import gsap from "gsap";
const quizes = ref(q);
const search = ref("");

watch(search, () => {
    quizes.value = q.filter((quiz) =>
        quiz.name.toLowerCase().includes(search.value.toLowerCase())
    );
});

const afterEnter = () => {};

const beforeEnter = (el) => {
    el.style.opacity = 0;
    el.style.transform = "TranslateY(-100px)";
};

const enter = (el) => {
    gsap.to(el, {
        y: 0,
        opacity: 1,
        duration: .7,
        delay: el.dataset.index * .3,
    });
};
</script>
<template>
    <div>
        <header>
            <h1>Quizes</h1>
            <input v-model.trim="search" type="text" placeholder="Search..." />
        </header>
        <div class="options-container">
            <TransitionGroup
                appear
                @before-enter="beforeEnter"
                @enter="enter"
                @after-enter="afterEnter"
            >
                <Card
                    v-for="(quiz, index) in quizes"
                    :key="quiz.id"
                    :quiz="quiz"
                    :data-index="index"
                />
            </TransitionGroup>
        </div>
    </div>
</template>

<style scoped>
header {
    margin-bottom: 10px;
    margin-top: 30px;
    display: flex;
    align-items: center;
}

header h1 {
    font-weight: bold;
    margin-right: 30px;
}

header input {
    border: none;
    background-color: rgba(128, 128, 128, 0.1);
    color: #fff;
    padding: 10px;
    border-radius: 5px;
}

.options-container {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    margin-top: 40px;
    gap: 2rem;
}
</style>
