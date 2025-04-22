<script setup lang="ts">
import { ref } from 'vue'
import DoubleFlipper from './components/DoubleFlipper.vue'
const time = ref(getTimeString())
const upperChar = ref(time.value)
const lowerChar = ref(time.value)
const duration = ref(0.5)

function getTimeString() {
  const date = new Date()
  return date.getHours().toString().padStart(2, '0') + date.getMinutes().toString().padStart(2, '0') + date.getSeconds().toString().padStart(2, '0')
}

setInterval(() => {
  time.value = getTimeString()
  upperChar.value = time.value
  setTimeout(() => {
    lowerChar.value = time.value
  }, duration.value * 1000)
}, 1000)

</script>

<template>
  <div class="flipper-container">
    <DoubleFlipper v-for="char, index in time" :key="index" :char="char" :duration="duration" />
  </div>
</template>

<style scoped>
.flipper-container {
  display: flex;
  align-items: center;
  justify-content: center;
}

.flipper-container>div {
  margin: 0 2px 0 2px;
}

.flipper-container>div:nth-child(even) {
  margin-right: 16px;
}

.flipper-container>div:first-child {
  margin-left: 0px;
}

.flipper-container>div:last-child {
  margin-right: 0px;
}
</style>
