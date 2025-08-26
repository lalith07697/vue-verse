<template>
  <section id="contact" class="py-20 bg-white dark:bg-gray-900">
    <div class="container mx-auto px-6 lg:px-20">
      <!-- Title -->
      <div class="text-center mb-12">
        <h2 class="text-3xl font-extrabold text-gray-900 dark:text-white sm:text-4xl">
          Connect with VueVerse
        </h2>
        <p class="mt-4 text-lg text-gray-600 dark:text-gray-300">
            We'd love to hear from you! Whether you have questions, feedback, feel free to reach out.
        </p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
        <!-- Contact Form -->
        <form
          @submit.prevent="onSubmit"
          class="space-y-6 bg-gray-50 dark:bg-gray-800 p-8 rounded-lg shadow-lg"
        >
          <div>
            <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
              >Name :-</label
            >
            <input
              type="text"
              name="name"
              placeholder="Enter your name"
              required
              class="w-full px-4 py-3 rounded-lg border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-green-500 dark:bg-gray-700 dark:text-white"
            />
          </div>
          <div>
            <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
              >Email :-</label
            >
            <input
              type="email"
              name="email"
              placeholder="Enter your email"
              required
              class="w-full px-4 py-3 rounded-lg border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-green-500 dark:bg-gray-700 dark:text-white"
            />
          </div>
          <div>
            <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
              >Message :-</label
            >
            <textarea
              name="message"
              rows="4"
              placeholder="Write your message..."
              required
              class="w-full px-4 py-3 rounded-lg border border-gray-300 dark:border-gray-600 focus:ring-2 focus:ring-green-500 dark:bg-gray-700 dark:text-white"
            ></textarea>
          </div>

          <!-- ✅ Fixed Contact Button -->
          <button
            type="submit"
            class="px-6 py-3 rounded-lg border border-gray-300 font-bold text-white hover:text-green-600 hover:border-green-600 transition"
            :disabled="contactLoading"
          >
            <span v-if="!contactLoading">Submit Now</span>
            <span v-else>Submitting...</span>
          </button>
        </form>

        <!-- Newsletter -->
        <div
          class="space-y-6 bg-gray-50 dark:bg-gray-800 p-8 rounded-lg h-max shadow-lg text-white"
        >
          <h3 class="text-2xl font-bold mb-4">Subscribe to our more...</h3>
          <p class="mb-6">Get the latest updates and offers directly to your inbox.</p>
          <form @submit.prevent="handleSubscribe" class="flex gap-3">
            <input
              type="email"
              name="email"
              placeholder="Enter your email"
              required
              class="flex-1 px-4 py-3 rounded-lg text-gray-300 focus:ring-2 focus:ring-green-500 dark:bg-gray-700 border border-gray-300"
            />

            <!-- ✅ Fixed Newsletter Button -->
            <button
              type="submit"
              class="px-6 py-3 rounded-lg border border-gray-300 font-bold text-white hover:text-green-600 hover:border-green-600 transition"
              :disabled="isLoading"
            >
              <span v-if="!isLoading">Subscribe</span>
              <span v-else>Subscribing...</span>
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const contactLoading = ref(false)
const isLoading = ref(false)

// ✅ Web3Forms submission for Contact Form
const onSubmit = async (event) => {
  contactLoading.value = true
  const formData = new FormData(event.target)
  formData.append('access_key', '2751ab29-0381-4eb2-9f0f-3b8f9547b91e') // Your Web3Forms API Key

  const object = Object.fromEntries(formData)
  const json = JSON.stringify(object)

  const res = await fetch('https://api.web3forms.com/submit', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      Accept: 'application/json',
    },
    body: json,
  }).then((res) => res.json())

  contactLoading.value = false

  if (res.success) {
    // alert('✅ Contact form submitted successfully!')
    event.target.reset()
  } else {
    // alert('❌ Something went wrong. Please try again!')
  }
}

const handleSubscribe = async (e) => {
  e.preventDefault()
  isLoading.value = true
  setTimeout(() => {
    isLoading.value = false
    // alert('🎉 You’re now subscribed to our newsletter!')
    e.target.reset()
  }, 2000)
}
</script>
