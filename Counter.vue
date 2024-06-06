<script setup>
import { ref } from 'vue'

const count = ref(0)

function increment() {
  count.value++
}

// Watchers
watch(count, (newCount, oldCount) => {
  console.log(`Count changed from ${oldCount} to ${newCount}`)
})
</script>

<template>
  <div @click="increment">
    Hello World no {{ count }}.
  </div>
</template>
