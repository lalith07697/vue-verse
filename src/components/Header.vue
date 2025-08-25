<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { Menu, X } from 'lucide-vue-next'
import logo from '../assets/favicon.jpg'
const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 20
}
// const scrollToSection = (sectionId: string) => {
const scrollToSection = () => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
  isMobileMenuOpen.value = false
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <header
    class="fixed top-0 left-0 right-0 z-50 transition-all duration-300"
    :class="
      isScrolled
        ? 'bg-white/95 backdrop-blur-lg shadow-md py-3 border-b border-gray-200'
        : 'bg-white/10 backdrop-blur-lg py-4 border-b border-white/10'
    "
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <nav class="flex items-center justify-between">
        <!-- Brand logo -->
        <div class="flex items-center gap-2 cursor-pointer">
          <img
            :src="logo"
            alt="App Logo"
            class="w-10 h-10 rounded-full shadow-md"
          />
          <span class="text-2xl font-extrabold text-green-600">VueVerse</span>
        </div>
        <!-- Desktop Nav -->
        <div class="hidden md:flex items-center gap-8">
          <a
            @click="scrollToSection('home')"
            class="relative text-gray-700 font-medium cursor-pointer hover:text-green-600 after:block after:w-0 after:h-0.5 after:bg-green-600 after:transition-all hover:after:w-full"
            >Home</a
          >
          <a
            @click="scrollToSection('about')"
            class="relative text-gray-700 font-medium cursor-pointer hover:text-green-600 after:block after:w-0 after:h-0.5 after:bg-green-600 after:transition-all hover:after:w-full"
            >About</a
          >
          <a
            @click="scrollToSection('events')"
            class="relative text-gray-700 font-medium cursor-pointer hover:text-green-600 after:block after:w-0 after:h-0.5 after:bg-green-600 after:transition-all hover:after:w-full"
            >Events</a
          >
          <a
            @click="scrollToSection('our-team')"
            class="relative text-gray-700 font-medium cursor-pointer hover:text-green-600 after:block after:w-0 after:h-0.5 after:bg-green-600 after:transition-all hover:after:w-full"
            >Our Team</a
          >
          <a
            @click="scrollToSection('partners')"
            class="relative text-gray-700 font-medium cursor-pointer hover:text-green-600 after:block after:w-0 after:h-0.5 after:bg-green-600 after:transition-all hover:after:w-full"
            >Partners</a
          >
          <a
            @click="scrollToSection('videos')"
            class="relative text-gray-700 font-medium cursor-pointer hover:text-green-600 after:block after:w-0 after:h-0.5 after:bg-green-600 after:transition-all hover:after:w-full"
            >Videos</a
          >
        </div>

        <!-- Actions -->
        <div class="flex items-center gap-4">
          <a
            href="#"
            class="hidden md:inline-block px-4 py-2 bg-green-600 text-white rounded-lg font-medium hover:bg-green-700 transition"
          >
            Join Us
          </a>
          <button @click="isMobileMenuOpen = !isMobileMenuOpen" class="md:hidden text-gray-700 p-2">
            <Menu v-if="!isMobileMenuOpen" :size="24" />
            <X v-else :size="24" />
          </button>
        </div>
      </nav>
    </div>

    <!-- Mobile Nav -->
    <div
      class="absolute top-full left-0 right-0 bg-white/95 backdrop-blur-lg border-b border-gray-200 transition-all duration-300"
      :class="
        isMobileMenuOpen
          ? 'opacity-100 visible translate-y-0'
          : 'opacity-0 invisible -translate-y-5'
      "
    >
      <div class="flex flex-col gap-4 px-6 py-6">
        <a
          @click="scrollToSection('home')"
          class="text-gray-700 font-medium cursor-pointer hover:text-green-600"
          >Home</a
        >
        <a
          @click="scrollToSection('about')"
          class="text-gray-700 font-medium cursor-pointer hover:text-green-600"
          >About</a
        >
        <a
          @click="scrollToSection('events')"
          class="text-gray-700 font-medium cursor-pointer hover:text-green-600"
          >Events</a
        >
        <a
          @click="scrollToSection('our-team')"
          class="text-gray-700 font-medium cursor-pointer hover:text-green-600"
          >Our Team</a
        >
        <a
          @click="scrollToSection('partners')"
          class="text-gray-700 font-medium cursor-pointer hover:text-green-600"
          >Partners</a
        >
        <a
          @click="scrollToSection('videos')"
          class="text-gray-700 font-medium cursor-pointer hover:text-green-600"
          >Videos</a
        >
        <a
          href="#"
          class="mt-4 inline-block px-4 py-2 bg-green-600 text-white rounded-lg font-medium hover:bg-green-700 transition"
        >
          Join Us
        </a>
      </div>
    </div>
  </header>
</template>
