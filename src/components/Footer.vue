<script setup>
const currentYear = new Date().getFullYear();
</script>

<template>
  <footer class="footer-section py-5 px-5">
    <div class="container-fluid d-flex flex-column align-items-center justify-content-center">
      
      <!-- Social Links -->
      <div class="social-links d-flex gap-4 mb-4">
        <a href="#" class="social-icon" aria-label="GitHub">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-github"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path></svg>
        </a>
        <a href="#" class="social-icon" aria-label="LinkedIn">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-linkedin"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"></path><rect x="2" y="9" width="4" height="12"></rect><circle cx="4" cy="4" r="2"></circle></svg>
        </a>
        <a href="#" class="social-icon" aria-label="Twitter">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-twitter"><path d="M23 3a10.9 10.9 0 0 1-3.14 1.53 4.48 4.48 0 0 0-7.86 3v1A10.66 10.66 0 0 1 3 4s-4 9 5 13a11.64 11.64 0 0 1-7 2c9 5 20 0 20-11.5a4.5 4.5 0 0 0-.08-.83A7.72 7.72 0 0 0 23 3z"></path></svg>
        </a>
        <a href="mailto:wajdijomaa9@gmail.com" class="social-icon" aria-label="Mail">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-mail"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path><polyline points="22,6 12,13 2,6"></polyline></svg>
        </a>
      </div>

      <!-- Copyright -->
      <div class="text-center text-white-50">
        <p class="mb-2">Designed & Built by Wajdi Jomaa</p>
        <p class="mb-0 small">&copy; {{ currentYear }} All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer-section {
  background: linear-gradient(to top, #000000 0%, #050505 100%);
  border-top: 1px solid rgba(255, 255, 255, 0.05);
  position: relative;
  overflow: hidden;
}

/* Glowing top border effect */
.footer-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 50%;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.5), transparent);
  box-shadow: 0 0 15px rgba(255, 255, 255, 0.3);
}

.social-icon {
  color: rgba(255, 255, 255, 0.6);
  transition: all 0.3s ease;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.05);
}

.social-icon:hover {
  color: #fff;
  transform: translateY(-3px);
  background: rgba(255, 255, 255, 0.1);
  box-shadow: 0 0 15px rgba(255, 255, 255, 0.3);
}

.social-icon svg {
  filter: drop-shadow(0 0 2px rgba(255, 255, 255, 0));
  transition: filter 0.3s ease;
}

.social-icon:hover svg {
  filter: drop-shadow(0 0 5px rgba(255, 255, 255, 0.5));
}
</style>
