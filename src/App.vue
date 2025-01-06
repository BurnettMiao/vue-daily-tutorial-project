<script setup>
import { ref } from 'vue'

import TodoDemo from '@/components/TodoDemo.vue'
import LifeCycle from '@/components/LifeCycle.vue'
import WatchDemo from '@/components/WatchDemo.vue'
import PropsDemo from '@/components/PropsDemo.vue'
import EemitsDemo from '@/components/EmitsDemo.vue'
import SlotDemo from '@/components/SlotDemo.vue'

const receiveOne = ref('no emit one')
const receiveTwo = ref(false)

const propOneMsg = ref()
const propTwoValue = ref()

function clickOne() {
  propOneMsg.value = 'click and props msg from parent'
}

function clickTwo() {
  propTwoValue.value = true
}
</script>

<template>
  <div class="container">
    <TodoDemo />

    <LifeCycle />

    <WatchDemo />

    <PropsDemo :propOne="propOneMsg" :propTwo="propTwoValue" />
    <button @click="clickOne">Prop One</button>
    <button @click="clickTwo">Prop Two</button>

    <EemitsDemo @emitOne="(data) => (receiveOne = data)" @emitTwo="(data) => (receiveTwo = data)" />
    <p>{{ receiveOne }}</p>
    <div :class="{ red: !receiveTwo, green: receiveTwo }">
      {{ receiveTwo ? 'eimt is true' : 'emit is false' }}
    </div>
    <!-- <div v-if="!receiveTwo" class="red">emit two is false</div>
    <div v-else class="green">emit two is true</div> -->

    <SlotDemo>
      <template v-slot:slot-title>Slot Title from parent</template>

      <template v-slot:slot-sentence>Slot Sentence from parent!</template>
    </SlotDemo>
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
  background-color: greenyellow;
}

.container {
  padding: 1rem;
}
</style>
