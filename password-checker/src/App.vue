<script setup>
import { computed, ref } from 'vue';
import './style.css';

const password = ref('')


const passwordChecker = computed(() => {
  const p = password.value

  let hasSpace = true
  if (/\s/.test(p)) {
    hasSpace = false
  }

  let hasRepeated = true
  for (let i = 0; i < p.length; i++) {
    if (p[i] === p[i + 1] && p[i] !== ' ') {
      hasRepeated = false
    }
  }

  return [
  {
    label: "8 or more characters.",
    valid: p.length >= 8
  },
  {
    label: "Digits",
    valid: (/\d/.test(p))
  },
  {
    label: "Uppercase.",
    valid: (/[A-Z]/.test(p))
  },
  {
    label: "Lowercase.",
    valid: (/[a-z]/.test(p))
  },
  {
    label: "Special characters.",
    valid: (/[!@#$%^&*]/.test(p))
  },
  {
    label: "Without spaces.",
    valid: hasSpace ? true : false
  },
  {
    label: "Repeated characters.",
    valid: hasRepeated ? true : false
  }
]})
</script>

<template>
  <main>
    <div class="card">
    <h1>Password Checker</h1>
      <label for="passwordInput">Check your password below:</label>
      <input type="password" v-model="password" autocomplete="off" />

      <div class="feedback">
        <ul>
          <li v-for="p in passwordChecker" :key="p.label">
            {{ p.label }}

            <span class="material-symbols-outlined" :style="{ color: p.valid ? 'green' : 'red' }">
              {{ p.valid ? 'check' : 'close' }}
            </span>
          </li>
        </ul>
      </div>
    </div>
  </main>
</template>

<style scoped>

.card {
  background-color: white;
  width: 21.875rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  padding: .9375rem;
  border-radius: 0.5rem;
}

ul {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 0.5rem;
}

ul li {
  list-style: none;
  display: flex;
  align-items: center;
}

</style>
