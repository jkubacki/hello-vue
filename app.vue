<script setup>
import { ref } from 'vue'

const inputText = ref('')
const count = ref(0)

function increment() {
  count.value++
}
</script>

<template>
  <div @click="increment">
    Hello World no {{ count }}.
  </div>
  
  <input v-model="inputText" />
  <p>{{ inputText }}</p>
</template>
