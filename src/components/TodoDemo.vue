<script setup>
import { ref, computed } from 'vue'

const id = ref(1)
const isCompleted = ref(false)
const newTodo = ref('')
const todos = ref([
  { id: id.value++, text: 'Learn HTML', done: true },
  { id: id.value++, text: 'Learn JavaScript', done: true },
  { id: id.value++, text: 'Learn Vue', done: false }
])

const filterTodos = computed(() => {
  return isCompleted.value ? todos.value.filter((t) => !t.done) : todos.value
})

function addTodo() {
  todos.value.push({ id: id.value++, text: newTodo.value, done: false })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <h2>Todos Demo</h2>

  <form @submit.prevent="addTodo">
    <input type="text" v-model="newTodo" required placeholder="new todo..." />
    <button>Add Todo</button>
  </form>

  <ul>
    <li v-for="todo in filterTodos" :key="todo.id">
      <input type="checkbox" />
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>

  <button @click="isCompleted = !isCompleted">
    {{ isCompleted ? 'Show All' : 'Hide Completed' }}
  </button>
</template>

<style scoped>
.done {
  color: gray;
  text-decoration: line-through;
}
</style>
