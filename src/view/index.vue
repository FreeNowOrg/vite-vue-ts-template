<template lang="pug">
h1 Home
p hello, wrold
</template>

<script setup lang="ts">
import { onMounted } from 'vue'
import { setTitle } from '../utils/setTitle'

onMounted(() => {
  setTitle()
})
</script>

<style scoped lang="sass"></style>