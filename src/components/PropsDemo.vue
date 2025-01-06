<script setup>
const props = defineProps({
  propOne: {
    type: String,
    default: 'no prop one yet'
  },
  propTwo: {
    type: Boolean,
    default: false
  }
})
</script>

<template>
  <h2>Props Demo</h2>
  <p>{{ props.propOne }}</p>
  <div :class="{ red: !props.propTwo, green: props.propTwo }">
    {{ propTwo ? 'prop is true' : 'prop is false' }}
  </div>
</template>

<style>
div {
  padding: 10px;
}

.red {
  background-color: brown;
}

.green {
  background-color: darkgreen;
}
</style>
