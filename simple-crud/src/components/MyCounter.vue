<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

const counterValue = ref(0)

const increaseCounter = () => {
  counterValue.value++;
}

const decreaseCounter = () => {
  counterValue.value--
}

const doubleValue = computed(function() {
  return counterValue.value * 2;
})

let timer = 0;

const start = () => {
  timer = setInterval(() => {
    increaseCounter();
  }, 1000);
}

const stop = () => {
  clearInterval(timer);
}

// Lifecycle Methods
onMounted(() => {
  start();
});

onUnmounted(() => {
  stop();
})
</script>

<template>
  <p>{{ counterValue }}</p>
  <button @click="counterValue++">Increase?</button>
  <button @click="decreaseCounter">Decrease?</button>
  <p>Double Value? => {{ doubleValue }}</p>

</template>
