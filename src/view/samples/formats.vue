<template lang="pug">
h1 Formats samples

h2 Headers
.card
  h1 h1
  h2 h2
  h3 h3
  h4 h4
  h5 h5

h2 Inline
p text <strong>bold</strong> <em>italic</em> <code>code</code>

h2 Block
.card
  p card
pre.
  Preformatted text
  Line break

h2 Flex List
.flex-list
  .list-item.card.header
    .key key
    .val val
  .list-item.card(v-for='item in 10')
    .key key-{{ item }}
    .val item-{{ item }}

h2 Info blocks
.info
  .title Info
  p Quick brown fox
.info.tips
  .title Tips
  p Quick brown fox
.info.warn
  .title Warn
  p Quick brown fox
.info.error
  .title Error
  p Quick brown fox
.info
</template>

<script setup lang="ts">
import { onMounted } from 'vue'
import { setTitle } from '../../utils/setTitle'
onMounted(() => {
  setTitle('Formats', 'Sample')
})
</script>

<style scoped lang="sass"></style>