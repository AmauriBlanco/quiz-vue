<script setup>
import { RouterView } from "vue-router";
</script>
<template>
    <div class="container">
        <Transition name="viewTransitions">
            <RouterView />
        </Transition>
    </div>
</template>

<style scoped>
.container {
    max-width: 1000px;
    padding: 0 15px;
    margin: 0 auto;
}

/*
.viewTransitions-enter-from{
    opacity: 0;
    transform: translateX(100px);
}

.viewTransitions-enter-to{
    opacity: 1;
    transform: translateX(0);
}

.viewTransitions-enter-active{
    transition: all 1s ease;
}
    */
</style>
