<script setup lang="ts">
const props = defineProps({
  count: Number
})
</script>

<template>
  <button>{{ count }}</button>
</template>

<style scoped></style>
