<script setup lang="ts">
import { usePerformanceRecorder } from '@vueuse/core'
import { ref } from 'vue'

const entrys = ref<PerformanceEntry[]>([])
usePerformanceRecorder({
  entryTypes: ['paint'],
}, (list) => {
  entrys.value = list.getEntries()
})
const refresh = () => window.location.reload()
</script>

<template>
  <button @click="refresh">
    refresh
  </button>

  <pre lang="json">{{ entrys }}</pre>
</template>
