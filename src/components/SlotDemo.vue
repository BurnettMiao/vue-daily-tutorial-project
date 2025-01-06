<script setup></script>

<template>
  <!-- slot 命名方式 kebab-case(短橫線)-->
  <h2>Slot Demo</h2>
  <h3 class="slot">
    <slot name="slot-title">No slot title yet!</slot>
  </h3>
  <p>
    <slot name="slot-sentence">No slot sentence yet!!</slot>
  </p>
</template>

<style scoped>
.slot {
  color: blueviolet;
}
</style>
