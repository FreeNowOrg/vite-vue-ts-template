<template lang="pug">
h1 Palette
.flex-list
  .list-item.card.header
    .key Color
    .val Preview
  .list-item.card(v-for='item in styles')
    .key <code>{{ item.key }}</code>
    .val
      .flex.gap-1
        span.color-block(:style='{ "background-color": item.val }')
        code {{ item.val }}
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue'
import { setTitle } from '../../utils/setTitle'

import sass from '../../styles/variables.sass'
const styles = ref([] as Record<string, any>[])

function init() {
  const css = sass as string
  css.split('\n').forEach((i) => {
    const t = i.trim()
    if (t.startsWith('--')) {
      const s = i.split(':')
      const key = s[0]
      const val = s[1].trim().replace(';', '')
      if (val.startsWith('#') || val.startsWith('rgb')) {
        styles.value = [...styles.value, { key, val }]
      }
    }
  })
  console.log()
}

onMounted(() => {
  setTitle('Palette', 'Sample')
  init()
})
</script>

<style scoped lang="sass">
.color-block
  display: inline-block
  border-radius: 50%
  width: 1.5rem
  height: 1.5rem
  box-shadow: 0 0 4px #aaa
</style>