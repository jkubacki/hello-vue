<script setup>
import { ref } from 'vue'

const count = ref(0)

function increment() {
  count.value++
}
</script>

<template>
  <div @click="increment">
    Hello World no {{ count }}.
  </div>
</template>
