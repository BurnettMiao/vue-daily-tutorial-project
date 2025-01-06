<script setup>
const emits = defineEmits(['emitOne', 'emitTwo'])

function clickOne() {
  emits('emitOne', 'click and emit one')
}

function clickTwo() {
  emits('emitTwo', true)
}
</script>

<template>
  <h2>Emits Demo</h2>
  <button @click="clickOne">Emit One</button>

  <button @click="clickTwo">Emit Two</button>
</template>
