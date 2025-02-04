<script setup></script>

<template>
  <!-- slot 命名方式 kebab-case(短橫線)-->
  <h2>Slot Demo</h2>
  <h3>
    <slot name="slot-title">No Slot Title yet!!</slot>
  </h3>
  <p>
    <slot name="slot-sentence">No slot sentence yet!</slot>
  </p>
</template>

<style scoped></style>
