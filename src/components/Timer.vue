<template>
  <div class="my-4">
    <button
      @click="toggleTimer"
      class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600"
    >
      {{ isRunning ? 'Stop' : 'Start' }} Timer
    </button>
    <p class="mt-2 text-lg">⏱️ Time: {{ elapsedTime }}s</p>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { onBeforeUnmount } from 'vue'

const emit = defineEmits<{
  (e: 'finished', time: number): void
}>()

const isRunning = ref(false)
const elapsedTime = ref(0)
let interval: number | undefined

function toggleTimer() {
  if (isRunning.value) {
    clearInterval(interval)
    emit('finished', elapsedTime.value)
  } else {
    elapsedTime.value = 0
    interval = setInterval(() => elapsedTime.value++, 1000)
  }
  isRunning.value = !isRunning.value
}

onBeforeUnmount(() => {
  clearInterval(interval)
})
</script>
