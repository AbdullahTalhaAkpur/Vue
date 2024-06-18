<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<template>
  <div>
    {{ count }}
    <button @click="count++">Count</button>
  </div>
</template>