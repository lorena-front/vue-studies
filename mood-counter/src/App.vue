<script setup>
import { computed, ref } from 'vue'

import iLoveHer from '@/assets/iloveher.jpg';
import iMissHer from '@/assets/imissher.jpg';
import itsFine from '@/assets/itsfine.jpg';

const counter = ref(0)

const increase = () => counter.value++ 
const decrease = () => counter.value--

const imageStatus = computed(() => {
  if (counter.value > 10 ) return iLoveHer
  if (counter.value < 0) return iMissHer
  return itsFine
})
</script>

<template>
  <div class="component">
    <h1>
      {{ counter }}
    </h1>

    <p v-if="counter > 10" style="color: pink;">
      Yes! I'm in love.
    </p>

    <p v-else-if="counter < 0" style="color: gray;">
      I want to see her.
    </p>

    <p v-else>
      It's fine.
    </p>

    <img :src="imageStatus" alt="Counter Status">

    <div class="buttons">
      <button @click="increase">+</button>
      <button @click="decrease">-</button>
    </div>
  </div>
</template>

<style scoped>
  img {
    width: 25%;
    height: auto;
  }
</style>
