<script setup>
// https://jsonplaceholder.typicode.com/todos
import { ref, watch } from 'vue'

const id = ref(1)
const todoData = ref('')

async function fetcData() {
  todoData.value = ''
  const res = await fetch(`https://jsonplaceholder.typicode.com/todos/${id.value}`)
  todoData.value = await res.json()
}

fetcData()
watch(id, fetcData)
</script>

<template>
  <h2>Watch Demo</h2>
  <p>Todos ID: {{ id }}</p>
  <button @click="id++">Fetch Next ID</button>
  <p v-if="!todoData">Load...</p>
  <pre v-else>{{ todoData }}</pre>
</template>

<style></style>
