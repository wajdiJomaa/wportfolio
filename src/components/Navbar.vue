<script setup>
import { ref } from 'vue';

const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>


<template>
<nav class="navbar navbar-expand-md navbar-dark py-3 px-5" style="background-color: #000000;">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Wajdi Jomaa</a>
    <button 
      class="navbar-toggler" 
      type="button" 
      @click="toggleMenu"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>
    <div 
      class="collapse navbar-collapse justify-content-end gap-4" 
      :class="{ 'show': isMenuOpen }"
      id="navbarNav"
    >
      <ul class="navbar-nav gap-3 align-items-center sm-center">
        <li class="nav-item active">
          <a class="nav-link" href="#home">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#projects">Projects</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#blogs">Blogs</a>
        </li>
      </ul>

      <div class="d-flex justify-content-center">
        <a href="mailto:wajdijomaa9@gmail.com" class="btn btn-outline-light">Contact me</a>
      </div>
    </div>
  </div>
</nav>
</template>

<style scoped>
.navbar {
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

@media (max-width: 768px) {
  .navbar-collapse {
    background: rgba(33, 37, 41, 0.95);
    position: absolute;
    top: 100%;
    right: 0;
    padding: 1rem;
    z-index: 1000;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  }
}

.nav-link {
  position: relative;
  color: rgba(255, 255, 255, 0.8) !important;
  transition: color 0.3s ease;
}

.nav-link::after {
  content: '';
  position: absolute;
  width: 0;
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: #fff;
  transition: width 0.3s ease;
}

.nav-link:hover {
  color: #fff !important;
}

.nav-link:hover::after {
  width: 100%;
}
</style>