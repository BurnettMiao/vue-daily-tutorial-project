<script setup>
import { ref, onMounted } from 'vue'

const pElementRef = ref(null)

onMounted(() => {
  pElementRef.value.textContent = 'ooooMounted!!'
})
</script>

<template>
  <h2>Life Cycle Demo</h2>

  <p ref="pElementRef">uuuuuuMounted!</p>
</template>

<style scoped></style>
