<script setup>
import { ref } from 'vue';

const item = ref('')
const items = ref([])

const addItem = () => {
  if (item.value !== '') {
    items.value.push(item.value)
    item.value = ''
  }
}

const deleteItem = (index) => {
  items.value.splice(index, 1)
}

</script>

<template>
  <input type="text" v-model="item" @keyup.enter="addItem" />
  <ul>
    <li v-for="(content, index) in items" :key="index">
      {{ content }} 
      <button @click="deleteItem(index)">Delete</button>
    </li>
  </ul>
</template>

<style scoped></style>
