<script setup>
import Header from './components/Header.vue'
import Home from './components/Home.vue'
import logo from './assets/favicon.jpg'
import { ref } from 'vue'
import { onMounted } from 'vue'
const isLoading = ref(true)

onMounted(() => {
  setTimeout(() => {
    isLoading.value = false
  }, 1000)
})
</script>

<template>
  <div class="min-h-screen">
    <!-- Loader of the main page-->
    <div
      v-if="isLoading"
      class="fixed inset-0 w-screen h-screen bg-gradient-to-br from-gray-50 to-gray-100 flex items-center justify-center z-[9999]"
    >
      <div class="text-center">
        <div class="inline-block animate-pulse">
          <img :src="logo" alt="App Logo" class="w-20 h-20 rounded-full shadow-lg" />
        </div>
        <!-- <h2 class="text-green-500 mt-4 font-bold text-lg">
          Loading VueVerse...
        </h2> -->
      </div>
    </div>

    <div v-else class="animate-fadeIn opacity-0">
      <Header />
      <Home />
    </div>
  </div>
</template>

<style>
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
.animate-fadeIn {
  animation: fadeIn 0.8s ease-in-out forwards;
}
</style>
