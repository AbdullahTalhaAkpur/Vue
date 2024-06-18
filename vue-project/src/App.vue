<script setup>
import JSConfetti from 'js-confetti'

const confetti = new JSConfetti()

function showConfetti() {
  confetti.addConfetti()
}
</script>

<template>
  <div>
    <h1 @click="showConfetti">
      🎉 Congratulations! 
    </h1>
  </div>
</template>

<style>
  h1 {
    text-align: center;
    cursor: pointer;
    margin-top: 3em;
  }
</style>