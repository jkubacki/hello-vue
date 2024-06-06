<script setup>
import { ref } from 'vue';
import Counter from './Counter.vue';

let id = 0
const todos = ref([
  { id: id++, text: 'Learn HTML', done: true},
  { id: id++, text: 'Learn JavaScript', done: true },
  { id: id++, text: 'Learn Vue', done: false }
])
const newTodo = ref('')

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}

// Template ref
const pElementRef = ref(null)

// Lifecycle hooks
onMounted(() => {
  pElementRef.value.textContent = 'Mounted!'
})
</script>

<template>
  <div>
    The app <span ref="pElementRef">not mounted</span>
  </div>
  <Counter :start-at="10" />
  
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" required placeholder="new todo">
    <button>Add Todo</button>
  </form>
  <p v-if="newTodo">New todo is: {{ newTodo }}</p>
  <p v-else>New todo is empty</p>

  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <input type="checkbox" v-model="todo.done">
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
</template>


<style>
.done {
  text-decoration: line-through;
}
</style>
