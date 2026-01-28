<script setup>
import { computed } from 'vue';

const _skillsRaw = [
  'Python', 'Java', 'SpringBoot', 'Flask', 
  'FastAPI', 'JavaScript', 'HTML', 'CSS', 'SQL', "MongoDB", "VueJs",
  "Linux", "Docker", "Postgresql", "NonSQL", "OOP", "BootStrap"
];

// Split skills for marquees
const halfIndex = Math.ceil(_skillsRaw.length / 2);
const firstHalf = _skillsRaw.slice(0, halfIndex);
const secondHalf = _skillsRaw.slice(halfIndex);

// Quadruple for smooth infinite scroll
const topMarqueeItems = computed(() => [...firstHalf, ...firstHalf, ...firstHalf, ...firstHalf]);
const bottomMarqueeItems = computed(() => [...secondHalf, ...secondHalf, ...secondHalf, ...secondHalf]);
</script>

<template>
<section id="home" class="hero-section d-flex align-items-center justify-content-center text-center p-5 position-relative">
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

    <!-- Marquees (Universal) -->
    <div class="skills-marquees">
      <!-- Top Marquee -->
      <div class="marquee-wrapper top-marquee">
        <div class="marquee-track">
          <div 
            v-for="(skill, index) in topMarqueeItems" 
            :key="`top-${index}`" 
            class="skill-bubble-fixed"
          >
            {{ skill }}
          </div>
        </div>
      </div>
      
      <!-- Bottom Marquee -->
      <div class="marquee-wrapper bottom-marquee">
        <div class="marquee-track reverse-track">
           <div 
            v-for="(skill, index) in bottomMarqueeItems" 
            :key="`btm-${index}`" 
            class="skill-bubble-fixed"
          >
            {{ skill }}
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  min-height: 700px;
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
  filter: drop-shadow(0 0 15px rgba(255, 255, 255, 0.3));
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

/* Skills Marquees */
.skills-marquees {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 1;
}

.marquee-wrapper {
  position: absolute;
  left: 0;
  width: 100%;
  overflow: hidden;
  display: flex;
  mask-image: linear-gradient(to right, transparent, black 15%, black 85%, transparent);
  -webkit-mask-image: linear-gradient(to right, transparent, black 15%, black 85%, transparent);
}

.top-marquee {
  top: 5%;
}

.bottom-marquee {
  bottom: 5%;
}

.marquee-track {
  display: flex;
  gap: 3rem;
  width: max-content;
  animation: scroll-track 40s linear infinite;
}

.reverse-track {
  animation: scroll-track-reverse 45s linear infinite;
}

.skill-bubble-fixed {
  color: #ffffff;
  opacity: 1;
  font-size: 1rem;
  font-weight: 500;
  font-family: 'JetBrains Mono', monospace;
  white-space: nowrap;
}

@keyframes scroll-track {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-50%);
  }
}

@keyframes scroll-track-reverse {
  from {
    transform: translateX(-50%);
  }
  to {
    transform: translateX(0);
  }
}

@media (max-width: 992px) {
  .top-marquee { top: 12%; }
  .bottom-marquee { bottom: 12%; }
  
  .skill-bubble-fixed {
     font-size: 0.9rem;
  }
}
</style>
