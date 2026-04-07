<script setup>
import { ref } from 'vue'

const counterValue = ref(0)

</script>

<template>
    <p>{{ counterValue }}</p>
    <button @click="counterValue++">Increase?</button>
</template>