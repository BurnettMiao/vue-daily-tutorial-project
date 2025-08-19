<script setup>
import { ref } from 'vue'

import VueOfficialTutorial from '@/components/VueOfficialTutorial.vue'
import SnakeGame from '@/components/SnakeGame.vue'

const showPage = ref(false)
</script>

<template>
  <div v-if="showPage">
    <VueOfficialTutorial />
  </div>

  <SnakeGame />
</template>

<style scoped></style>
