<script setup>
defineProps({
  title: String,
  description: String,
  technologies: Array,
  image: String,
  link: String
});
</script>

<template>
  <div class="project-card">
    <div class="image-container" v-if="image">
      <img :src="image" :alt="title" loading="lazy" />
    </div>
    <div class="content">
      <h3 class="title">{{ title }}</h3>
      <p class="description">{{ description }}</p>
      
      <div class="technologies">
        <span v-for="tech in technologies" :key="tech" class="tech-tag">{{ tech }}</span>
      </div>

      <a v-if="link" :href="link" target="_blank" class="project-link">
        View Project <span>&nearr;</span>
      </a>
    </div>
  </div>
</template>

<style scoped>
.project-card {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 16px;
  overflow: hidden;
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  display: flex;
  flex-direction: column;
  height: 100%;
  backdrop-filter: blur(10px);
}

.project-card:hover {
  transform: translateY(-10px);
  border-color: rgba(255, 255, 255, 0.3);
  background: rgba(255, 255, 255, 0.06);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);
}

.image-container {
  height: 200px;
  overflow: hidden;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}

.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.project-card:hover .image-container img {
  transform: scale(1.05);
}

.content {
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.title {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: #fff;
}

.description {
  color: #aaa;
  font-size: 0.95rem;
  line-height: 1.6;
  margin-bottom: 1.5rem;
  flex-grow: 1;
}

.technologies {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.tech-tag {
  font-size: 0.75rem;
  padding: 4px 10px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  color: #ddd;
  font-family: 'JetBrains Mono', monospace;
}

.project-link {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  color: #fff;
  text-decoration: none;
  font-weight: 600;
  margin-top: auto;
  transition: color 0.3s ease;
}

.project-link:hover {
  color: #ccc;
}

.project-link span {
  transition: transform 0.3s ease;
}

.project-link:hover span {
  transform: translate(2px, -2px);
}
</style>
