<script setup>
import { ref } from 'vue'

import DrinkOrder from '@/components/DrinkOrder.vue'

import TodoDemo from '@/components/TodoDemo.vue'
import LifeCycle from '@/components/LifeCycle.vue'
import WatchDemo from '@/components/WatchDemo.vue'
import PropsDemo from '@/components/PropsDemo.vue'
import EmitsDemo from '@/components/EmitsDemo.vue'
import SlotDemo from '@/components/SlotDemo.vue'

const emitSentence = ref('No emit yet!!')
const emitBoolean = ref(false)

const propOneMsg = ref()
const propTwoMsg = ref()

function clickPropOne() {
  propOneMsg.value = 'Prop Msg from parenet!!'
}
function clickPropTwo() {
  propTwoMsg.value = true
}
</script>

<template>
  <div class="container">
    <DrinkOrder />

    <hr class="margin-space" />

    <TodoDemo />

    <hr class="margin-space" />

    <LifeCycle />

    <hr class="margin-space" />

    <WatchDemo />

    <hr class="margin-space" />

    <PropsDemo :propOne="propOneMsg" :propTwo="propTwoMsg" />
    <button @click="clickPropOne">Prop One</button>
    <button @click="clickPropTwo">Prop Two</button>

    <hr class="margin-space" />

    <EmitsDemo @emitOne="(msg) => (emitSentence = msg)" @emitTwo="(msg) => (emitBoolean = msg)" />
    <p>{{ emitSentence }}</p>
    <div class="emitDiv" :class="{ emitDivTrue: emitBoolean, emitDivFalse: !emitBoolean }">
      {{ emitBoolean ? 'Emit is true' : 'Emit is false' }}
    </div>

    <hr class="margin-space" />

    <SlotDemo>
      <template v-slot:slot-title> Slot Title from Parent!! </template>

      <template v-slot:slot-sentence> slot sentence from parent components! </template>
    </SlotDemo>
  </div>
</template>

<style scoped>
.emitDiv {
  padding: 10px;
}

.emitDivTrue {
  background-color: cadetblue;
  color: #000;
}
.emitDivFalse {
  background-color: brown;
  color: #000;
}

.margin-space {
  margin-block: 1rem;
}
</style>
