<script setup>
defineProps({
  title: String,
  date: String,
  description: String,
  tags: Array,
  link: String
})
</script>

<template>
  <div class="blog-card">
    <div class="card-content">
      <div class="meta-top">
        <span class="date">{{ date }}</span>
      </div>
      <h3 class="title">{{ title }}</h3>
      <p class="description">{{ description }}</p>
      
      <div class="footer">
        <div class="tags">
          <span v-for="tag in tags" :key="tag" class="tag">#{{ tag }}</span>
        </div>
        <a :href="link" class="read-more" target="_blank">
          Read Article
          <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="arrow"><line x1="5" y1="12" x2="19" y2="12"></line><polyline points="12 5 19 12 12 19"></polyline></svg>
        </a>
      </div>
    </div>
    <div class="glow-effect"></div>
  </div>
</template>

<style scoped>
.blog-card {
  position: relative;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 16px;
  padding: 2rem;
  overflow: hidden;
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  display: flex;
  flex-direction: column;
  height: 100%;
  backdrop-filter: blur(10px);
}

.blog-card:hover {
  transform: translateY(-5px);
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(255, 255, 255, 0.2);
  box-shadow: 0 10px 30px -10px rgba(0, 0, 0, 0.5);
}

.meta-top {
  margin-bottom: 1rem;
}

.date {
  font-size: 0.85rem;
  color: #888;
  font-family: 'JetBrains Mono', monospace;
  background: rgba(255, 255, 255, 0.05);
  padding: 4px 10px;
  border-radius: 20px;
}

.title {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 0.75rem;
  background: linear-gradient(90deg, #fff, #ccc);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  line-height: 1.3;
}

.description {
  color: #aaa;
  font-size: 0.95rem;
  line-height: 1.6;
  margin-bottom: 1.5rem;
  flex-grow: 1;
}

.footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: auto;
}

.tags {
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
}

.tag {
  font-size: 0.75rem;
  color: #666;
  transition: color 0.3s;
}

.blog-card:hover .tag {
  color: #888;
}

.read-more {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: #fff;
  text-decoration: none;
  font-weight: 500;
  font-size: 0.9rem;
  position: relative;
  transition: gap 0.3s;
}

.read-more:hover {
  gap: 0.8rem;
}

.arrow {
  transition: transform 0.3s;
}

.glow-effect {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle at 50% -20%, rgba(255, 255, 255, 0.1), transparent 70%);
  opacity: 0;
  transition: opacity 0.5s;
  pointer-events: none;
}

.blog-card:hover .glow-effect {
  opacity: 1;
}
</style>
