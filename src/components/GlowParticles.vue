<script setup>
const particles = Array.from({ length: 60 }, (_, i) => ({
  id: i,
  style: {
    top: `${Math.random() * 100}%`,
    left: `${Math.random() * 100}%`,
    animationDuration: `${Math.random() * 10 + 10}s`,
    animationDelay: `${Math.random() * 5}s`
  }
}));
</script>

<template>
  <div class="particles-container">
    <div 
      v-for="particle in particles" 
      :key="particle.id" 
      class="particle"
      :style="particle.style"
    ></div>
  </div>
</template>

<style scoped>
.particles-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 0;
  overflow: hidden;
}

.particle {
  position: absolute;
  width: 5px;
  height: 5px;
  background: #ffffff;
  border-radius: 50%;
  box-shadow: 0 0 30px rgba(255, 255, 255, 1), 0 0 60px rgba(255, 255, 255, 0.9);
  opacity: 0;
  animation: float linear infinite;
}

@keyframes float {
  0% {
    transform: translate(0, 0) scale(1);
    opacity: 0;
  }
  20% {
    opacity: 0.8;
    transform: translate(20px, -20px) scale(1.2);
  }
  80% {
    opacity: 0.4;
    transform: translate(-20px, 20px) scale(0.8);
  }
  100% {
    transform: translate(0, 0) scale(1);
    opacity: 0;
  }
}
</style>
