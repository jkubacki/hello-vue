<script setup>
import { ref } from 'vue';

const props = defineProps({
  startAt: Number
})

const count = ref(props.startAt)

const emit = defineEmits(['response'])
function increment() {
  count.value++
  emit('response', `Incremented to ${count.value}`)
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
