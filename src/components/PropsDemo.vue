<script setup>
const props = defineProps({
  propOne: {
    type: String,
    default: 'No props yet!!'
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
  <p class="propDiv" :class="{ propTrue: props.propTwo, propFalse: !props.propTwo }">
    {{ props.propTwo ? 'Props is true' : 'Props is false' }}
  </p>
</template>

<style>
.propDiv {
  padding: 10px;
}

.propTrue {
  background-color: cadetblue;
  color: #fff;
}

.propFalse {
  background-color: brown;
  color: #fff;
}
</style>
