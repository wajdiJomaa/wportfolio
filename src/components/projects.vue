<script setup>
import ProjectCard from './project.vue';

const projects = [
  {
    title: 'Modern Portfolio',
    description: 'A simplistic, highly polished portfolio website built with Vue 3 and Vite.',
    technologies: ['Vue 3', 'Vite', 'CSS', 'Anime.js'],
    link: '#',
    image: 'https://via.placeholder.com/600x400/222/fff?text=Project+1'
  },
  {
    title: 'E-Commerce Platform',
    description: 'Scalable e-commerce solution with cart functionality and payment integration.',
    technologies: ['React', 'Node.js', 'Express', 'MongoDB'],
    link: '#',
    image: 'https://via.placeholder.com/600x400/333/fff?text=Project+2'
  },
  {
    title: 'Task Management App',
    description: 'Productivity tool for teams to manage tasks and collaborate in real-time.',
    technologies: ['Angular', 'Firebase', 'Material UI'],
    link: '#',
    image: 'https://via.placeholder.com/600x400/444/fff?text=Project+3'
  }
];
</script>

<template>
  <section class="projects-section container py-5">
    <div class="row mb-4">
      <div class="col-12 text-start">
        <h2 class="display-4 fw-bold text-white mb-2">Selected Works</h2>
        <p class="text-muted lead mb-3" style="max-width: 600px;">
          A showcase of projects that demonstrate my passion for clean code and intuitive design.
        </p>
        <a href="#" class="btn btn-outline-light rounded-pill px-4">View All Projects</a>
      </div>
    </div>
      
    <div class="row g-4 justify-content-center">
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
</style>
