<script setup>

import { ref, computed } from 'vue';

const num = ref(0);

const greenNum = computed(() => num.value > 0);
const redNum = computed(() => num.value < 0);
const normalNum = computed(() => num.value === 0);

const increment = () => {
    num.value++;
}

const decrement = () => {
    num.value--;
}

const reset = () => {
    num.value = 0;
}

</script>

<template>

    <div class="container">
        <div class="counter">
            <span class="lbl">Count: <span :class="{green: greenNum, red: redNum, normal: normalNum}">{{ num }}</span></span>
        </div>
        <div class="buttons">
            <button @click="increment">Increment</button>
            <button @click="decrement">Decrement</button>
            <button @click="reset">Reset</button>
        </div>
    </div>

</template>

<style scoped>

:root {
  --bg: #0a0e1a;
  --surface: #131a2b;
  --border: #1f2a44;
  --text: #e6ebf5;
  --text-dim: #8a96b2;
  --accent: #4a7cff;
}

.container {
    margin-top: 3rem;
    display: flex;
    flex-direction: column;
    gap: 2rem;
    align-items: center;
}

.buttons {
    display: flex;
    gap: 1.5rem;
}

.buttons button {
    width: 125px;
    padding: 1rem;
    border-radius: 5px;
    border: none;
    cursor: pointer;
    font-size: 16px;
    background-color: var(--accent);
    font-weight: 600;
    transition: .2s ease;
}

.buttons button:hover {
    background-color: #4070ea;
}

.buttons button:active {
    background-color: #355ec7;
}

.counter .lbl {
    color: var(--text);
    font-size: 25px;
    font-weight: 600;
}

.green {
    color: darkgreen;
}

.red {
    color: darkred;
}

.normal {
    color: var(--text);
}


</style>