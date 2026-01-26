<script setup>
import { onMounted } from 'vue';
import anime from 'animejs';

const skills = [
  'Python', 'Java', 'SpringBoot', 'Flask', 
  'FastAPI', 'JavaScript', 'HTML', 'CSS', 'SQL', "MongoDB", "VueJs",
  "Linux", "Docker", "Postgresql", "NonSQL", "OOP", "BootStrap"
];

const animateBubble = (el) => {
  const xRange = window.innerWidth / 3;
  const yRange = window.innerHeight / 3;

  anime({
    targets: el,
    translateX: () => anime.random(-xRange, xRange),
    translateY: () => anime.random(-yRange, yRange),
    scale: () => anime.random(0.8, 1),
    duration: () => anime.random(2000, 4000),
    delay: () => anime.random(0, 200),
    easing: 'easeInOutQuad',
    direction: 'alternate',
    loop: true
  });
};

onMounted(() => {
  const bubbles = document.querySelectorAll('.skill-bubble');
  bubbles.forEach(bubble => animateBubble(bubble));
});
</script>

<template>
  <section class="hero-section d-flex align-items-center justify-content-center text-center p-5 position-relative">
    <div class="content-wrapper position-relative" style="z-index: 2;">
      <h1 class="name mb-3">Wajdi Jomaa</h1>
      <p class="description mb-4">
        Full Stack Developer<br>
        <span class="sub-text">Crafting digital experiences with code and creativity.</span>
      </p>
      
      <div class="action-buttons fade-in-up">
        <button class="btn btn-outline-light rounded-pill px-5 py-3 me-3">View Work</button>
        <button class="btn btn-light rounded-pill px-5 py-3 text-dark fw-bold">Contact Me</button>
      </div>
    </div>

    <!-- Skill Bubbles -->
    <div class="bubbles-container">
      <div 
        v-for="(skill, index) in skills" 
        :key="skill" 
        class="skill-bubble"
        :style="index % 2 === 0
  ? { left: Math.random() * 40 + '%', top: Math.random() * 70 + '%' }
  : { right: Math.random() * 40 + '%', top: Math.random() * 70 + '%' }
"
      >
        {{ skill }}
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  min-height: 600px;
  color: white;
  overflow: hidden; /* Keep bubbles inside */
}

.name {
  font-size: clamp(4rem, 10vw, 7rem);
  font-weight: 800;
  letter-spacing: -3px;
  background: linear-gradient(90deg, #555, #fff, #555);
  background-size: 200% auto;
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  opacity: 0;
  animation: slideUpFade 1s ease-out 0.2s forwards, shimmer 3s linear infinite;
}

@keyframes shimmer {
  to {
    background-position: 200% center;
  }
}

.description {
  font-size: 1.5rem;
  color: #ccc;
  opacity: 0;
  animation: slideUpFade 1s ease-out 0.5s forwards;
}

.sub-text {
  font-size: 1rem;
  color: #888;
  display: block;
  margin-top: 0.5rem;
}

/* Bubbles */
.bubbles-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none; /* Let clicks pass through */
  z-index: 1;
}

.skill-bubble {
  position: absolute;
  padding: 12px 24px;
  border: 1px solid rgba(255, 255, 255, 0.25);
  border-top: 1px solid rgba(255, 255, 255, 0.5); /* Extra shine on top */
  border-radius: 50px;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.02));
  backdrop-filter: blur(10px);
  color: #fff;
  font-size: 0.95rem;
  font-weight: 500;
  font-family: 'JetBrains Mono', monospace;
  white-space: nowrap;
  box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.3), inset 0 0 10px rgba(255, 255, 255, 0.05);
  text-shadow: 0 0 10px rgba(255, 255, 255, 0.2);
}

/* Animations */
@keyframes slideUpFade {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.action-buttons {
  opacity: 0;
  animation: fadeIn 1s ease-out 0.8s forwards;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
