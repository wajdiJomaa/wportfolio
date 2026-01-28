<script setup>
import ProjectCard from './project.vue';
import { ref, onMounted, onUnmounted } from 'vue';

const projects = [
  // ... existing projects ...
  {
    title: 'SHELL',
    description: 'A POSIX like Shell built using Python with various functionalities built-in commands, execute from PATH, redirect, pipeline, autocomplete, history',
    technologies: ['Python', 'OS', 'Bash'],
    link: '#',
    image: '/images/shell.png'
  },
  {
    title: 'E-Commerce Platform',
    description: 'An E-Store for small business, with admin management panel and flexible layout for customers to filter and order products.',
    technologies: ['Flask', 'Jinja', 'Sqlite', 'HTMX'],
    link: '#',
    image: '/images/ecommerce.png'
  },
  {
    title: 'CHIP-8 Emulator',
    description: 'An Emulator for the CHIP-8 virtual machine built using python and SDL',
    technologies: ['Python', 'Emulator', 'SDL'],
    link: '#',
    image: '/images/chip8.png'
  }
];

const observer = ref(null);

onMounted(() => {
  observer.value = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.scroll-animate').forEach(el => {
    observer.value.observe(el);
  });
});

onUnmounted(() => {
  if (observer.value) observer.value.disconnect();
});
</script>

<template>
  <section id="projects" class="projects-section container-fluid py-4 px-5 scroll-animate">
    <div class="row mb-5">
      <div class="col-12 text-start">
        <h2 class="display-5 fw-bold animated-title mb-4">Selected Works</h2>
        <div>
          <a href="#" class="btn btn-outline-light rounded-pill px-4">View All Projects</a>
        </div>
      </div>
    </div>
      
    <div class="row g-4 justify-content-start">
      <div v-for="(project, index) in projects" :key="index" class="col-md-6 col-lg-4">
        <ProjectCard
          :title="project.title"
          :description="project.description"
          :technologies="project.technologies"
          :image="project.image"
          :link="project.link"
        />
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects-section {
  position: relative;
  z-index: 2;
}

.scroll-animate {
  opacity: 0;
  transform: translateY(50px);
  transition: all 1s ease-out;
}

.scroll-animate.visible {
  opacity: 1;
  transform: translateY(0);
}


.animated-title {
  background: linear-gradient(90deg, #fff, #888, #fff);
  background-size: 200% auto;
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: shimmer 3s linear infinite;
  display: inline-block;
}

@keyframes shimmer {
  to {
    background-position: 200% center;
  }
}
</style>
