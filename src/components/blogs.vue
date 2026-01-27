<script setup>
import Blog from './blog.vue'
import { ref, onMounted, onUnmounted } from 'vue'

const blogs = ref([
  // ... existing blogs data ...
  {
    title: "Understanding Vue 3 Composition API",
    date: "Jan 15, 2026",
    description: "A deep dive into the new Composition API in Vue 3 and how it changes the way we write scalable Vue components.",
    tags: ["Vue", "JavaScript", "Frontend"],
    link: "#"
  },
  {
    title: "The Future of Web Development with AI",
    date: "Dec 22, 2025",
    description: "Exploring how Artificial Intelligence is reshaping the landscape of web development, from code generation to dynamic UIs.",
    tags: ["AI", "Tech", "Future"],
    link: "#"
  },
  {
    title: "Optimizing Reactivity in Modern Apps",
    date: "Nov 10, 2025",
    description: "Tips and tricks for ensuring your web applications remain performant and reactive even with heavy data loads.",
    tags: ["Performance", "Web", "Optimization"],
    link: "#"
  }
])

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
  <section id="blogs" class="blogs-section container-fluid py-5 px-5 scroll-animate">
    <div class="row mb-5">
      <div class="col-12 text-start">
        <h2 class="display-5 fw-bold animated-title mb-4">Latest Articles</h2>
        <div>
          <a href="#" class="btn btn-outline-light rounded-pill px-4">View All Blogs</a>
        </div>
      </div>
    </div>
    
    <div class="blogs-grid">
      <Blog
        v-for="(blog, index) in blogs"
        :key="index"
        v-bind="blog"
        class="blog-item"
      />
    </div>
  </section>
</template>

<style scoped>
.blogs-section {
  /* Subtle distinction from pure black body */
  background: linear-gradient(to bottom, #000000 0%, #0a0a0a 100%);
  position: relative;
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

.blogs-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
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
