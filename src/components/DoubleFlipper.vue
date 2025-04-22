<script setup lang="ts">
import { ref, watch } from 'vue';
import SingleFlipper from './SingleFlipper.vue';

const props = defineProps<{
    char: string
    duration?: number
}>()

const upperChar = ref(props.char)
const lowerChar = ref(props.char)
watch(() => props.char, (newVal) => {
    upperChar.value = newVal
    setTimeout(() => {
        lowerChar.value = newVal
    }, props.duration ? props.duration * 500 : 500)
})

</script>

<template>
    <div class="double-char-container">
        <SingleFlipper :char="upperChar.toString()" flipper-direction="upper"
            :duration="duration ? duration / 2 : 0.5" />
        <SingleFlipper :char="lowerChar.toString()" flipper-direction="lower"
            :duration="duration ? duration / 2 : 0.5" />
    </div>
</template>

<style scoped>
.double-char-container {
    display: flex;
    flex-direction: column;
}

.double-char-container>div {
    margin-top: 5px;
}

.double-char-container>div:first-child {
    margin-top: 0px;
}
</style>
