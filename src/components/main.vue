<script setup>
import { onMounted, onUnmounted, ref, computed } from 'vue';
import anime from 'animejs';

const _skillsRaw = [
  'Python', 'Java', 'SpringBoot', 'Flask', 
  'FastAPI', 'JavaScript', 'HTML', 'CSS', 'SQL', "MongoDB", "VueJs",
  "Linux", "Docker", "Postgresql", "NonSQL", "OOP", "BootStrap"
];

const skillsRaw = _skillsRaw.concat(_skillsRaw)

const isMobile = ref(false);

const checkMobile = () => {
  isMobile.value = window.innerWidth <= 768;
};

// Duplicate skills on mobile for seamless looping
const items = computed(() => {
  return isMobile.value ? [...skillsRaw, ...skillsRaw] : skillsRaw;
});

const getBubbleStyle = (index) => {
  if (isMobile.value) {
    // CSS handles positioning on mobile
    return {};
  }

  // Desktop styles (randomly placed left/right)
  return index % 2 === 0
    ? { left: Math.random() * 50 + '%', top: Math.random() * 80 + '%' }
    : { right: Math.random() * 50 + '%', top: Math.random() * 80 + '%' };
};

const animateBubble = (el) => {
  const xRange = window.innerWidth / 10;
  const yRange = window.innerHeight / 10;
  const duration = anime.random(6000, 10000); // Slower movement

  anime({
    targets: el,
    translateX: () => anime.random(-xRange, xRange),
    translateY: () => anime.random(-yRange, yRange),
    scale: () => anime.random(0.6, 0.8),
    opacity: [
       { value: [0, 1], duration: duration * 0.1, easing: 'linear' },
       { value: 1, duration: duration * 0.8 },
       { value: 0, duration: duration * 0.1, easing: 'linear' }
    ],
    duration: duration,
    delay: () => anime.random(2000, 5000),
    easing: 'easeInOutQuad',
    direction: 'alternate',
    loop: true
  });
};

onMounted(() => {
  checkMobile();
  window.addEventListener('resize', checkMobile);

  // Only run anime.js on desktop
  if (!isMobile.value) {
    const bubbles = document.querySelectorAll('.skill-bubble');
    // Initialize opacity to 0
    bubbles.forEach(b => b.style.opacity = 0);
    bubbles.forEach(bubble => animateBubble(bubble));
  }
});

onUnmounted(() => {
  window.removeEventListener('resize', checkMobile);
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
      <div class="marquee-track">
        <div 
          v-for="(skill, index) in items" 
          :key="`${skill}-${index}`" 
          class="skill-bubble"
          :style="getBubbleStyle(index)"
        >
          {{ skill }}
        </div>
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

/* Bubbles Container */
.bubbles-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none; /* Let clicks pass through */
  z-index: 1;
  /* Hide bubbles behind the central text */
  -webkit-mask-image: radial-gradient(ellipse at center, transparent 30%, black 70%);
  mask-image: radial-gradient(ellipse at center, transparent 30%, black 70%);
}

/* Track Wrapper */
.marquee-track {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
}

.skill-bubble {
  position: absolute;
  padding: 8px 16px;
  border: 1px solid rgba(255, 255, 255, 0.25);
  border-top: 1px solid rgba(255, 255, 255, 0.5); /* Extra shine on top */
  border-radius: 50px;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.02));
  backdrop-filter: blur(10px);
  color: #fff;
  font-size: 0.8rem;
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

@media (max-width: 768px) {
  .bubbles-container {
    position: absolute;
    top: auto;
    bottom: 15%; /* Position strip */
    left: 0;
    width: 100%;
    height: auto;
    overflow: hidden;
    mask-image: linear-gradient(to right, transparent, black 10%, black 90%, transparent);
    -webkit-mask-image: linear-gradient(to right, transparent, black 10%, black 90%, transparent);
  }

  /* Make track a flexible row that moves */
  .marquee-track {
    position: relative;
    display: flex;
    gap: 3rem;
    width: max-content; /* Allow content to dictate width */
    animation: scroll-track 20s linear infinite; /* Animate the whole track */
  }

  .skill-bubble {
    position: relative; /* Reset absolute */
    inset: auto !important;
    transform: none !important;
    
    /* Thin text style */
    padding: 0;
    border: none;
    background: transparent;
    border-radius: 0;
    box-shadow: none;
    backdrop-filter: none;
    
    color: rgba(255, 255, 255, 0.6);
    font-size: 0.9rem;
    font-weight: 300;
    
    flex-shrink: 0;
  }

  .skill-bubble:nth-child(n+9) {
    display: block;
  }
}

@keyframes scroll-track {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-50%); /* Move half the total width (the length of one full set) */
  }
}
</style>
