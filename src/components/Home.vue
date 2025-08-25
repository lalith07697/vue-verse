<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { ChevronRight, Users, Code, Heart } from 'lucide-vue-next'

const animateCount = (target: number, duration: number = 2000) => {
  const start = 0
  const startTime = Date.now()
  const countRef = ref(0)

  const animate = () => {
    const elapsed = Date.now() - startTime
    const progress = Math.min(elapsed / duration, 1)
    
    countRef.value = Math.floor(start + (target - start) * progress)
    
    if (progress < 1) {
      requestAnimationFrame(animate)
    }
  }

  requestAnimationFrame(animate)
  return countRef
}

const membersCount = animateCount(2500)
const projectsCount = animateCount(150)
const eventsCount = animateCount(25)

onMounted(() => {
  // Start animations on mount
})
</script>

<template>
  <section id="home" class="hero">
    <div class="hero-background">
      <div class="bg-pattern"></div>
      <div class="floating-elements">
        <div class="floating-element" style="--delay: 0s; --duration: 20s;">
          <div class="vue-icon">
            <svg width="40" height="40" viewBox="0 0 261.76 226.69">
              <g transform="matrix(1.3333 0 0 -1.3333 -76.311 313.34)">
                <g transform="translate(178.06 235.01)">
                  <path d="m0 0-22.669-39.264-22.669 39.264h-75.491l98.16-170.02 98.16 170.02z" fill="var(--vue-green)"/>
                </g>
              </g>
            </svg>
          </div>
        </div>
        <div class="floating-element" style="--delay: 5s; --duration: 25s;">
          <Code :size="32" color="var(--vue-blue)" />
        </div>
        <div class="floating-element" style="--delay: 10s; --duration: 18s;">
          <Users :size="36" color="var(--accent)" />
        </div>
        <div class="floating-element" style="--delay: 15s; --duration: 22s;">
          <Heart :size="28" color="var(--success)" />
        </div>
      </div>
    </div>
    
    <div class="container-wide">
      <div class="hero-content">
        <div class="hero-text">
          <div class="hero-badge animate-fadeInUp" style="animation-delay: 0.2s;">
            <span class="badge-text">Welcome to the Future of Vue Development</span>
          </div>
          
          <h1 class="hero-title animate-fadeInUp" style="animation-delay: 0.4s;">
            Join the <span class="gradient-text">VueVerse</span> Community
          </h1>
          
          <p class="hero-subtitle animate-fadeInUp" style="animation-delay: 0.6s;">
            Connect with passionate Vue.js developers, share knowledge, build amazing projects, and grow your skills in the most vibrant Vue community on the web.
          </p>
          
          <div class="hero-actions animate-fadeInUp" style="animation-delay: 0.8s;">
            <a href="#" class="btn btn-primary btn-large">
              Join Community
              <ChevronRight :size="20" />
            </a>
            <a href="#about" class="btn btn-ghost btn-large">
              Learn More
            </a>
          </div>
        </div>
        
        <div class="hero-stats animate-fadeInUp" style="animation-delay: 1s;">
          <div class="stat-item">
            <div class="stat-number">{{ membersCount.toLocaleString() }}+</div>
            <div class="stat-label">Active Members</div>
          </div>
          <div class="stat-item">
            <div class="stat-number">{{ projectsCount }}+</div>
            <div class="stat-label">Projects Shared</div>
          </div>
          <div class="stat-item">
            <div class="stat-number">{{ eventsCount }}+</div>
            <div class="stat-label">Events Hosted</div>
          </div>
        </div>
      </div>
      
      <div class="hero-visual animate-fadeInUp" style="animation-delay: 1.2s;">
        <div class="hero-image">
          <img 
            src="https://images.pexels.com/photos/7988086/pexels-photo-7988086.jpeg?auto=compress&cs=tinysrgb&w=800" 
            alt="Vue developers collaborating"
            class="main-image"
          />
          <div class="image-overlay">
            <div class="overlay-content">
              <div class="pulse-dot"></div>
              <span class="live-indicator">Live Community</span>
            </div>
          </div>
        </div>
        
        <div class="hero-cards">
          <div class="hero-card card-1">
            <div class="card-icon">
              <Users :size="24" />
            </div>
            <div class="card-content">
              <h4>Active Community</h4>
              <p>24/7 support & discussions</p>
            </div>
          </div>
          
          <div class="hero-card card-2">
            <div class="card-icon">
              <Code :size="24" />
            </div>
            <div class="card-content">
              <h4>Learn & Share</h4>
              <p>Code reviews & best practices</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
  background: linear-gradient(135deg, 
    rgba(79, 192, 141, 0.05) 0%, 
    rgba(255, 255, 255, 0.95) 50%, 
    rgba(66, 184, 131, 0.05) 100%
  );
  padding: 8rem 0 4rem;
}

.hero-background {
  position: absolute;
  inset: 0;
  z-index: -2;
}

.bg-pattern {
  position: absolute;
  inset: 0;
  background: 
    radial-gradient(circle at 25% 25%, rgba(79, 192, 141, 0.1) 0%, transparent 50%),
    radial-gradient(circle at 75% 75%, rgba(255, 107, 107, 0.1) 0%, transparent 50%);
}

.floating-elements {
  position: absolute;
  inset: 0;
}

.floating-element {
  position: absolute;
  opacity: 0.6;
  animation: float var(--duration) infinite ease-in-out;
  animation-delay: var(--delay);
}

.floating-element:nth-child(1) { top: 20%; left: 10%; }
.floating-element:nth-child(2) { top: 60%; right: 15%; }
.floating-element:nth-child(3) { bottom: 30%; left: 20%; }
.floating-element:nth-child(4) { top: 40%; right: 30%; }

@keyframes float {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  25% { transform: translateY(-20px) rotate(5deg); }
  50% { transform: translateY(-10px) rotate(-3deg); }
  75% { transform: translateY(-15px) rotate(2deg); }
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr;
  gap: 3rem;
  align-items: center;
  text-align: center;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  padding: 0.5rem 1rem;
  background: rgba(79, 192, 141, 0.1);
  border: 1px solid rgba(79, 192, 141, 0.3);
  border-radius: 50px;
  margin-bottom: 1.5rem;
}

.badge-text {
  font-size: 0.875rem;
  font-weight: 500;
  color: var(--vue-green-dark);
}

.hero-title {
  font-size: 3rem;
  font-weight: 800;
  line-height: 1.1;
  color: var(--gray-900);
  margin-bottom: 1.5rem;
}

.gradient-text {
  background: linear-gradient(135deg, var(--vue-green) 0%, var(--vue-blue) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-subtitle {
  font-size: 1.25rem;
  line-height: 1.6;
  color: var(--gray-600);
  margin-bottom: 2rem;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.hero-actions {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
  margin-bottom: 3rem;
}

.btn-large {
  padding: 1rem 2rem;
  font-size: 1rem;
  gap: 0.5rem;
}

.hero-stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
  max-width: 600px;
  margin: 0 auto;
}

.stat-item {
  text-align: center;
}

.stat-number {
  font-size: 2rem;
  font-weight: 800;
  color: var(--vue-green);
  margin-bottom: 0.5rem;
}

.stat-label {
  color: var(--gray-600);
  font-weight: 500;
}

.hero-visual {
  position: relative;
  display: none;
}

.hero-image {
  position: relative;
  border-radius: 1rem;
  overflow: hidden;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

.main-image {
  width: 100%;
  height: 400px;
  object-fit: cover;
}

.image-overlay {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(10px);
  padding: 0.75rem 1rem;
  border-radius: 50px;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.pulse-dot {
  width: 8px;
  height: 8px;
  background: var(--success);
  border-radius: 50%;
  animation: pulse 2s infinite;
}

.live-indicator {
  font-size: 0.875rem;
  font-weight: 600;
  color: var(--gray-700);
}

.hero-cards {
  position: absolute;
  inset: 0;
}

.hero-card {
  position: absolute;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(20px);
  padding: 1rem;
  border-radius: 0.75rem;
  display: flex;
  align-items: center;
  gap: 0.75rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.3);
  min-width: 200px;
}

.card-1 {
  top: -1rem;
  left: -2rem;
  animation: float 6s infinite ease-in-out;
}

.card-2 {
  bottom: -1rem;
  right: -2rem;
  animation: float 6s infinite ease-in-out reverse;
}

.card-icon {
  flex-shrink: 0;
  width: 40px;
  height: 40px;
  background: var(--vue-green);
  color: white;
  border-radius: 0.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.card-content h4 {
  font-size: 0.875rem;
  font-weight: 600;
  color: var(--gray-800);
  margin-bottom: 0.25rem;
}

.card-content p {
  font-size: 0.75rem;
  color: var(--gray-600);
}

@media (min-width: 768px) {
  .hero-title {
    font-size: 4rem;
  }
  
  .hero-content {
    text-align: left;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
  }
  
  .hero-subtitle {
    margin-left: 0;
    margin-right: 0;
  }
  
  .hero-actions {
    justify-content: flex-start;
  }
  
  .hero-stats {
    margin: 0;
  }
  
  .hero-visual {
    display: block;
  }
}

@media (min-width: 1024px) {
  .hero-title {
    font-size: 5rem;
  }
}
</style>