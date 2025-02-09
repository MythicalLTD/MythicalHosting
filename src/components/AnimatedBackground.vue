<template>
  <div class="fixed inset-0 pointer-events-none overflow-hidden">
    <div v-for="i in 3" :key="i" class="nebula"></div>
    <div v-for="i in 100" :key="`star-${i}`" class="star"></div>
    <div v-for="i in 20" :key="`comet-${i}`" class="comet"></div>
  </div>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'

onMounted(() => {
  const nebulas = document.querySelectorAll('.nebula')
  const stars = document.querySelectorAll('.star')
  const comets = document.querySelectorAll('.comet')

  nebulas.forEach((nebula, index) => {
    const nebulaElement = nebula as HTMLElement
    nebulaElement.style.top = `${Math.random() * 100}%`
    nebulaElement.style.left = `${Math.random() * 100}%`
    nebulaElement.style.animationDelay = `${index * 10}s`
  })

  stars.forEach(star => {
    const starElement = star as HTMLElement
    starElement.style.top = `${Math.random() * 100}%`
    starElement.style.left = `${Math.random() * 100}%`
    starElement.style.animationDuration = `${Math.random() * 3 + 2}s`
    starElement.style.animationDelay = `${Math.random() * 3}s`
  })

  comets.forEach(comet => {
    const cometElement = comet as HTMLElement
    cometElement.style.top = `${Math.random() * 100}%`
    cometElement.style.left = `${Math.random() * 100}%`
    cometElement.style.animationDuration = `${Math.random() * 10 + 10}s`
    cometElement.style.animationDelay = `${Math.random() * 20}s`
  })
})
</script>

<style scoped>
.nebula {
  position: absolute;
  width: 24rem;
  height: 24rem;
  border-radius: 9999px;
  opacity: 0.2;
  filter: blur(3xl);
  background: radial-gradient(circle, rgba(124, 58, 237, 0.5) 0%, rgba(192, 38, 211, 0.2) 70%, transparent 100%);
  animation: float 20s ease-in-out infinite;
}

.star {
  position: absolute;
  width: 0.25rem;
  height: 0.25rem;
  background-color: white;
  border-radius: 9999px;
  animation: twinkle 3s infinite;
}

.comet {
  position: absolute;
  width: 0.25rem;
  height: 0.25rem;
  background-color: white;
  border-radius: 9999px;
  box-shadow: 0 0 20px 2px white;
  animation: comet 20s linear infinite;
}

@keyframes float {
  0%, 100% { transform: translate(0, 0); }
  50% { transform: translate(50px, 50px); }
}

@keyframes twinkle {
  0%, 100% { opacity: 1; transform: scale(1); }
  50% { opacity: 0.5; transform: scale(0.5); }
}

@keyframes comet {
  0% { transform: translateX(0) translateY(0); opacity: 1; }
  70% { opacity: 1; }
  100% { transform: translateX(1000px) translateY(1000px); opacity: 0; }
}
</style>
