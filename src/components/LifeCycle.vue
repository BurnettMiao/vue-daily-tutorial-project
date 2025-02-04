<script setup>
import { ref, onMounted } from 'vue'

const pElementRef = ref(null)

onMounted(() => {
  pElementRef.value.textContent = 'ooMoumted!!'
})
</script>

<template>
  <h2>Life Cycle</h2>
  <p ref="pElementRef">uuuuuMounted!!</p>
</template>

<style scoped></style>
