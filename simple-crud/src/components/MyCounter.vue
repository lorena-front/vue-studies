<script setup>
import { ref, computed, customRef } from 'vue'

const counterValue = ref(0)

const decreaseCounter = () => {
  counterValue.value--;
}

const doubleValue = computed(function() {
  return counterValue.value * 2;
})

// let timer = 0;

// const start = () => {
//   timer = setInterval(() => {
//     increaseCounter();
//   }, 1000);
// }

// const stop = () => {
//   clearInterval(timer);
// }

// // Lifecycle Methods
// onMounted(() => {
//   start();
// });

// onUnmounted(() => {
//   stop();
// })

// Create a custom reference (customRef)
const count = customRef((track, trigger) => {
  let value = 0;  // value will be the variable being tracked,initialized here to 0.
  return {
    get() {
      // Track the dependency when the value is read.
      track();
      console.log("get value =", value);
      return value;
    },
    set(newValue) {
      // Update the value and trigger reactivity.
      value = newValue;
      trigger();
      console.log("set value =", value);
    }
  };
});

const increaseCounter = () => {
  console.log("A")
  count.value++;
  console.log("B")
}
</script>

<template>
  <p>{{ counterValue }}</p>
  <p>{{ count }}</p>
  <button @click="increaseCounter">Increase?</button>
  <button @click="decreaseCounter">Decrease?</button>
  <p>Double Value? => {{ doubleValue }}</p>

</template>
