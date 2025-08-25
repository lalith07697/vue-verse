<template>
  <section
    id="home"
    class="relative flex items-center min-h-screen overflow-hidden py-32 bg-gradient-to-br from-green-200/10 via-white/95 to-green-200/10"
  >
    <!-- Background -->
    <div class="absolute inset-0 -z-10">
      <div
        class="absolute inset-0 bg-[radial-gradient(circle_at_25%_25%,rgba(79,192,141,0.1)_0%,transparent_50%),radial-gradient(circle_at_75%_75%,rgba(255,107,107,0.1)_0%,transparent_50%)]"
      ></div>
    </div>

    <!-- Content -->
    <div
      class="container mx-auto px-6 lg:px-12 grid grid-cols-1 lg:grid-cols-2 gap-12 items-center"
    >
      <!-- Text -->
      <div class="text-center lg:text-left space-y-6">
        <!-- Badge -->
        <div
          class="inline-flex items-center px-4 py-2 rounded-full border border-green-400/50 bg-green-100/20 animate-fadeInUp"
        >
          <span class="text-sm font-medium text-green-700">
            Welcome to the Future of Vue Development
          </span>
        </div>

        <!-- Title -->
        <h1
          class="text-4xl md:text-5xl lg:text-6xl font-extrabold text-gray-900 leading-tight animate-fadeInUp"
        >
          Join the
          <span class="bg-gradient-to-r from-green-500 to-blue-500 bg-clip-text text-transparent">
            VueVerse
          </span>
          Community
        </h1>

        <!-- Subtitle -->
        <p class="text-lg text-gray-600 max-w-xl mx-auto lg:mx-0 animate-fadeInUp">
          Connect with passionate Vue.js developers, share knowledge, build amazing projects, and
          grow your skills in the most vibrant Vue community on the web.
        </p>

        <!-- Buttons -->
        <div class="flex flex-wrap justify-center lg:justify-start gap-4 animate-fadeInUp">
          <a
            href="#"
            class="flex items-center gap-2 px-6 py-3 rounded-lg bg-green-600 text-white font-medium hover:bg-green-700 transition"
          >
            Join Community <ChevronRight :size="20" />
          </a>
          <a
            href="#about"
            class="px-6 py-3 rounded-lg border border-gray-300 text-gray-700 font-medium hover:text-green-600 hover:border-green-600 transition"
          >
            Learn More
          </a>
        </div>

        <!-- Stats -->
        <div class="grid grid-cols-3 gap-8 max-w-md mx-auto lg:mx-0 animate-fadeInUp">
          <div class="text-center">
            <div class="text-3xl font-extrabold text-green-600">
              {{ membersCount.toLocaleString() }}+
            </div>
            <div class="text-gray-600 font-medium">Active Members</div>
          </div>
          <div class="text-center">
            <div class="text-3xl font-extrabold text-green-600">{{ projectsCount }}+</div>
            <div class="text-gray-600 font-medium">Projects Shared</div>
          </div>
          <div class="text-center">
            <div class="text-3xl font-extrabold text-green-600">{{ eventsCount }}+</div>
            <div class="text-gray-600 font-medium">Events Hosted</div>
          </div>
        </div>
      </div>

      <!-- Visual -->
      <div class="relative hidden lg:block animate-fadeInUp">
        <div class="rounded-xl overflow-hidden shadow-2xl relative">
          <img
            src="https://images.pexels.com/photos/7988086/pexels-photo-7988086.jpeg?auto=compress&cs=tinysrgb&w=800"
            alt="Vue developers collaborating"
            class="w-full h-[400px] object-cover"
          />

          <!-- Overlay -->
          <div
            class="absolute top-4 right-4 flex items-center gap-2 bg-white/90 backdrop-blur-md px-3 py-2 rounded-full shadow-md"
          >
            <div class="w-2 h-2 rounded-full bg-green-500 animate-pulse"></div>
            <span class="text-sm font-semibold text-gray-700"> Live Community </span>
          </div>
        </div>

        <!-- Floating Cards -->
        <div
          class="absolute -top-6 -left-8 bg-white/90 backdrop-blur-xl p-4 rounded-lg shadow-lg flex items-center gap-3 border border-white/30 animate-float-fast"
        >
          <div
            class="w-10 h-10 rounded-md bg-green-500 text-white flex items-center justify-center"
          >
            <Users :size="20" />
          </div>
          <div>
            <h4 class="text-sm font-semibold text-gray-800">Active Community</h4>
            <p class="text-xs text-gray-600">24/7 support & discussions</p>
          </div>
        </div>

        <div
          class="absolute -bottom-6 -right-8 bg-white/90 backdrop-blur-xl p-4 rounded-lg shadow-lg flex items-center gap-3 border border-white/30 animate-float-slower"
        >
          <div
            class="w-10 h-10 rounded-md bg-green-500 text-white flex items-center justify-center"
          >
            <Code :size="20" />
          </div>
          <div>
            <h4 class="text-sm font-semibold text-gray-800">Learn & Share</h4>
            <p class="text-xs text-gray-600">Code reviews & best practices</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import { ChevronRight, Users, Code, Heart } from 'lucide-vue-next'

const membersCount = ref(1200)
const projectsCount = ref(350)
const eventsCount = ref(45)
</script>

<style scoped>
/* 🌊 Floating Animation (smooth & playful) */
@keyframes float {
  0% {
    transform: translateY(0px) translateX(0px) rotate(0deg);
  }
  25% {
    transform: translateY(-15px) translateX(6px) rotate(3deg);
  }
  50% {
    transform: translateY(-25px) translateX(0px) rotate(-2deg);
  }
  75% {
    transform: translateY(-15px) translateX(-6px) rotate(2deg);
  }
  100% {
    transform: translateY(0px) translateX(0px) rotate(0deg);
  }
}

.animate-float {
  animation: float 12s ease-in-out infinite;
}
.animate-float-slow {
  animation: float 12s ease-in-out infinite;
}
.animate-float-slower {
  animation: float 22s ease-in-out infinite;
}
.animate-float-fast {
  animation: float 8s ease-in-out infinite;
}
</style>
