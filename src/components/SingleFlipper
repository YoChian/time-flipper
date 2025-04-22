<script setup lang="ts">

defineProps<{
  char: string
  flipperDirection: 'upper' | 'lower'
  duration?: number
}>()

</script>

<template>
  <div class="flipper-container">
    <Transition>
      <div :key="char" :class="['flipper', flipperDirection === 'lower' ? 'flipper-lower' : 'flipper-upper']"
        :style="{ '--duration': `${duration ?? 0.5}s` }">
        <div class="char-container orbitron-numbers">{{ char }}</div>
      </div>
    </Transition>
  </div>
</template>

<style scoped>
.flipper-container {
  position: relative;
  width: 100px;
  height: 50px;
}

.flipper {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #f0f0f0;
  display: flex;
  justify-content: center;
  overflow: hidden;
  z-index: 0;
}

.flipper-upper {
  align-items: flex-start;
  border-radius: 8px 8px 4px 4px;
  transform: rotateX(0deg);
  transform-origin: bottom center;
}

.flipper-lower {
  align-items: flex-end;
  border-radius: 4px 4px 8px 8px;
  transform: rotateX(0deg);
  transform-origin: top center;
}

.v-enter-active,
.v-leave-active {
  transition: transform var(--duration) linear, filter var(--duration) linear;
}

.v-enter-from.flipper-upper {
  z-index: -1;
}

.v-enter-from.flipper-lower {
  transform: rotateX(-90deg);
  filter: brightness(1.05);
  z-index: 1;
}

.v-leave-to.flipper-upper {
  transform: rotateX(90deg);
  filter: brightness(0.8);
  z-index: 1;
}

.char-container {
  font-size: 5em;
  color: #333;
  height: 100px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}


.orbitron-numbers {
  font-family: "Orbitron", sans-serif;
  font-optical-sizing: auto;
  font-weight: 400;
  font-style: normal;
}
</style>