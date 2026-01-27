<script setup>
import ProjectCard from './project.vue';

const projects = [
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
</script>

<template>
  <section class="projects-section container-fluid py-4 px-5">
    <div class="row mb-5">
      <div class="col-12 text-start">
        <h2 class="display-5 fw-bold text-white">Selected Works</h2>
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
