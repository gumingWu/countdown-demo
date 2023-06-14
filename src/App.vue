<script setup lang="ts">
import CountDown from './components/CountDown.vue'

function callback() {
  console.log('callback')
}
</script>

<template>
  <CountDown :count="20" @callback="callback" />
</template>

<style scoped>
</style>
