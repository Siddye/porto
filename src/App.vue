<script setup>
import { ref } from 'vue';
import profileImg from '../profile.png';

const docImages = [
  'Screenshot 2026-05-16 190318.png',
  'Screenshot 2026-05-16 190356.png',
  'Screenshot 2026-05-18 103429.png',
  'Screenshot 2026-05-18 104237.png',
  'Screenshot 2026-05-25 090752.png',
  'Screenshot 2026-05-25 101652.png',
  'Screenshot 2026-06-08 105511.png',
  'Screenshot 2026-06-08 105538.png',
  'Screenshot 2026-06-15 082208.png',
  'Screenshot 2026-06-15 083656.png',
  'Screenshot 2026-06-15 083822.png',
  'Screenshot 2026-06-15 084016.png',
  'Screenshot 2026-06-15 121852.png',
  'Screenshot 2026-06-15 122011.png',
  'Screenshot 2026-06-15 122134.png',
  'Screenshot 2026-06-15 122146.png'
];

const activeImage = ref(null);
const sliderRef = ref(null);

const slide = (direction) => {
  if (sliderRef.value) {
    const scrollAmount = 350; // Scroll distance
    if (direction === 'left') {
      sliderRef.value.scrollBy({ left: -scrollAmount, behavior: 'smooth' });
    } else {
      sliderRef.value.scrollBy({ left: scrollAmount, behavior: 'smooth' });
    }
  }
};

const openLightbox = (img) => {
  activeImage.value = img;
  document.body.style.overflow = 'hidden';
};

const closeLightbox = () => {
  activeImage.value = null;
  document.body.style.overflow = 'auto';
};
</script>

<template>
  <div class="portfolio">
    <!-- Japanese Accent Background Text -->
    <div class="japanese-accent">ポートフォリオ</div>
    
    <!-- Animated Background Orbs -->
    <div class="orb orb-1"></div>
    <div class="orb orb-2"></div>
    <div class="orb orb-3"></div>

    <div class="container">
      <!-- Hero Section -->
      <header class="section hero">
        <div class="avatar-container">
          <img :src="profileImg" alt="Avatar" class="avatar" />
          <div class="avatar-ring"></div>
        </div>
        <p class="subtitle">こんにちは、私は</p>
        <h1>Raffi Cassidy Chandra</h1>
        <p class="username">@Sidco</p>
        <p class="description">
          Sid | Software Engineer & Game Developer <br/>
          Building games, crafting stories, and learning new things every day. <br/>
          Current quest: turning ideas into reality.
        </p>
        <div class="hero-actions">
          <a href="https://github.com/Siddye" target="_blank" class="github-btn">
            <svg class="github-icon" viewBox="0 0 24 24" width="20" height="20">
              <path fill="currentColor" d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.53 1.032 1.53 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"/>
            </svg>
            GitHub Profile
          </a>
        </div>
      </header>

      <!-- Tech Stack Section -->
      <section class="section tech">
        <h2>Tech Stack</h2>
        <div class="tech-stack">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg" alt="HTML" class="tech-icon" title="HTML5" />
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg" alt="CSS" class="tech-icon" title="CSS3" />
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg" alt="JavaScript" class="tech-icon" title="JavaScript" />
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original.svg" alt="Python" class="tech-icon" title="Python" />
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/java/java-original.svg" alt="Java" class="tech-icon" title="Java" />
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/php/php-original.svg" alt="PHP" class="tech-icon" title="PHP" />
        </div>
      </section>

      <!-- Documentation Gallery Section (Slider) -->
      <section class="section gallery">
        <div class="gallery-header">
          <h2>Dokumentasi Ngoding</h2>
          <div class="slider-controls">
            <button class="slider-btn prev-btn" @click="slide('left')" aria-label="Slide Left">←</button>
            <button class="slider-btn next-btn" @click="slide('right')" aria-label="Slide Right">→</button>
          </div>
        </div>
        <div class="gallery-slider" ref="sliderRef">
          <div 
            v-for="(img, idx) in docImages" 
            :key="idx" 
            class="gallery-item"
            @click="openLightbox(img)"
          >
            <img :src="'/dokumentasi/' + img" :alt="'Dokumentasi ' + (idx + 1)" loading="lazy" />
            <div class="gallery-overlay">
              <span>🔍 Perbesar</span>
            </div>
          </div>
        </div>
      </section>

      <!-- Certificates Section -->
      <section class="section certificates">
        <h2>Sertifikat & Pencapaian</h2>
        <div class="cert-list">
          <!-- Item 1 -->
          <a href="/sertifikat_course_123_3262563_191125193718.pdf" target="_blank" class="cert-link">
            <div class="cert-icon">🌸</div>
            <div class="cert-content">
              <h3>Belajar Dasar Pemrograman Web</h3>
              <p>Sertifikat Kelulusan</p>
            </div>
            <div class="cert-arrow">→</div>
          </a>
          
          <!-- Item 2 -->
          <a href="/sertifikat_course_256_3262563_271125075538.pdf" target="_blank" class="cert-link">
            <div class="cert-icon">⛩️</div>
            <div class="cert-content">
              <h3>Belajar Dasar Pemrograman Javascript</h3>
              <p>Sertifikat Kelulusan</p>
            </div>
            <div class="cert-arrow">→</div>
          </a>
          
          <!-- Item 3 -->
          <a href="/sertifikat_course_315_3262563_031225205318.pdf" target="_blank" class="cert-link">
            <div class="cert-icon">✨</div>
            <div class="cert-content">
              <h3>Belajar Membuat Front-END untuk Pemula</h3>
              <p>Sertifikat Kelulusan</p>
            </div>
            <div class="cert-arrow">→</div>
          </a>
        </div>
      </section>
      
      <!-- Footer -->
      <footer class="footer">
        <p>© 2026 @Sidyco. Dibuat dengan 💜 & Vue.js</p>
      </footer>
    </div>

    <!-- Lightbox Modal -->
    <div v-if="activeImage" class="lightbox" @click="closeLightbox">
      <div class="lightbox-content" @click.stop>
        <img :src="'/dokumentasi/' + activeImage" alt="Zoomed Dokumentasi" />
        <button class="lightbox-close" @click="closeLightbox">✕</button>
      </div>
    </div>
  </div>
</template>

<style>
/* We import our global styles in style.css, so it affects this component. */
</style>
