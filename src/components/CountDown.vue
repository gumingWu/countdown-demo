<script setup lang="ts">
import { computed, ref } from 'vue'

const props = withDefaults(defineProps<{
  count?: number
}>(), {
  count: 10,
})
const emits = defineEmits(['callback'])

const countRef = ref(props.count)
const countZero = computed(() => {
  return countRef.value === 0
})

let frame = 0
let start = 0
function decrease() {
  let end = performance.now()
  if(end - start >= 1000) {
    countRef.value = countRef.value - 1
    start = end
  }
  if(!countRef.value) {
    window.cancelAnimationFrame(frame)
    return
  }

  frame = window.requestAnimationFrame(decrease)
}

decrease()
</script>

<template>
  <button :disabled="!countZero" @click="emits('callback')">
    <div v-if="!countZero">倒计时：{{ countRef }}</div>
    <div v-else>开抢啦！</div>
  </button>
</template>

<style scoped></style>
