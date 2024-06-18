<script setup>
import { ref, onMounted, computed } from 'vue'

const duration = ref(15 * 1000)
const elapsed = ref(0)

let lastTime
let handle

const update = () => {
  elapsed.value = performance.now() - lastTime
  if (elapsed.value >= duration.value) {
    cancelAnimationFrame(handle)
  } else {
    handle = requestAnimationFrame(update)
  }
}

const reset = () => {
  elapsed.value = 0
  lastTime = performance.now()
  update()
}

const progressRate = computed(() => 
Math.min(elapsed.value / duration.value, 1))

reset()

onMounted(() => {
  cancelAnimationFrame(handle)
})
</script>

<template>
  <div>
    <label>
     Elapsed Time: <progress :value="progressRate"></progress>
    </label>
      <div>{{ (elapsed / 1000).toFixed(1) }}s</div>
    <div>Duration: <input type="range" v-model="duration" min="1" max="30000">
    {{ (duration / 1000).toFixed(1) }}s
    </div>

    <button @click="reset">Reset</button>
  </div>    
</template>

<style>
 .elapsed-bar {
  background-color: red;
  width: 300px;
 }
</style>