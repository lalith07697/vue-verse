<script setup lang="ts">
import { Calendar, Clock, Users, MapPin, ExternalLink } from 'lucide-vue-next'
import { ref } from 'vue'
const upcomingEvents = [
  {
    id: 1,
    title: 'Vue 3 Composition API Deep Dive',
    date: '2025-09-15',
    time: '2:00 PM PST',
    type: 'Workshop',
    attendees: 245,
    location: 'Online',
    description: 'Master the Composition API with hands-on exercises and real-world examples.',
    image:
      'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRZofSFW4yiF4XMgKFdX969sL13_qY-pX8cEA&s',
    featured: true,
    moreinfo: 'Hello world',
  },
  {
    id: 2,
    title: 'VueVerse Monthly Meetup',
    date: '2025-09-22',
    time: '6:00 PM EST',
    type: 'Meetup',
    attendees: 189,
    location: 'Virtual',
    description: 'Join our monthly community meetup for networking and Vue.js discussions.',
    image:
      'https://images.pexels.com/photos/7988079/pexels-photo-7988079.jpeg?auto=compress&cs=tinysrgb&w=800',
    moreinfo: 'Hello world',
  },
  {
    id: 3,
    title: 'Building Scalable Vue Apps',
    date: '2025-010-01',
    time: '10:00 AM GMT',
    type: 'Webinar',
    attendees: 156,
    location: 'Online',
    description: 'Learn best practices for building large-scale Vue.js applications.',
    image:
      'https://images.pexels.com/photos/3184433/pexels-photo-3184433.jpeg?auto=compress&cs=tinysrgb&w=800',
    moreinfo: 'Hello world',
  },
]

const pastEvents = [
  { title: 'Vue 3 Migration Strategies', date: '2025-01-18', attendees: 310, rating: 4.9 },
  { title: 'Pinia State Management', date: '2025-01-10', attendees: 275, rating: 4.8 },
  { title: 'Vue Testing Fundamentals', date: '2024-12-20', attendees: 198, rating: 4.7 },
]

const isModelopen = ref(false)
const modelOpened = () => {
  isModelopen.value = true
}
const modelClosed = () => {
  isModelopen.value = false
}
</script>

<template>
  <section id="events" class="py-24 bg-gradient-to-br from-white/80 via-emerald-100/10 to-white/80">
    <div class="container mx-auto px-6 lg:px-12">
      <!-- Section Header -->
      <div class="text-center mb-16 animate-fadeInUp">
        <h2 class="text-4xl md:text-5xl font-extrabold text-gray-900 mb-4">Upcoming Events</h2>
        <p class="text-lg text-gray-600 max-w-2xl mx-auto">
          Join our exclusive events, workshops, and meetups to level up your Vue.js skills and
          connect with the community.
        </p>
      </div>

      <!-- Featured Event -->
      <div
        class="bg-white/90 backdrop-blur-lg rounded-2xl overflow-hidden mb-16 shadow-xl border border-white/40 grid md:grid-cols-2 animate-fadeInUp"
      >
        <div class="relative h-72 md:h-auto">
          <img
            :src="upcomingEvents[0].image"
            :alt="upcomingEvents[0].title"
            class="w-full h-full object-cover"
          />
          <div
            class="absolute top-4 left-4 bg-emerald-500 text-white text-sm font-semibold px-4 py-1 rounded-full"
          >
            Featured
          </div>
        </div>

        <div class="p-8 flex flex-col justify-center">
          <div class="flex gap-3 mb-4">
            <span class="bg-blue-500 text-white text-sm font-medium px-3 py-1 rounded-full">{{
              upcomingEvents[0].type
            }}</span>
            <span class="bg-gray-100 text-gray-700 text-sm font-medium px-3 py-1 rounded-full">
              {{
                new Date(upcomingEvents[0].date).toLocaleDateString('en-US', {
                  month: 'short',
                  day: 'numeric',
                })
              }}
            </span>
          </div>

          <h3 class="text-2xl md:text-3xl font-bold text-gray-900 mb-4">
            {{ upcomingEvents[0].title }}
          </h3>
          <p class="text-gray-600 mb-6">{{ upcomingEvents[0].description }}</p>

          <div class="grid md:grid-cols-2 gap-3 mb-6 text-gray-600 text-sm">
            <div class="flex items-center gap-2">
              <Calendar />
              {{
                new Date(upcomingEvents[0].date).toLocaleDateString('en-US', {
                  weekday: 'long',
                  month: 'long',
                  day: 'numeric',
                })
              }}
            </div>
            <div class="flex items-center gap-2"><Clock /> {{ upcomingEvents[0].time }}</div>
            <div class="flex items-center gap-2"><MapPin /> {{ upcomingEvents[0].location }}</div>
            <div class="flex items-center gap-2">
              <Users /> {{ upcomingEvents[0].attendees }} attending
            </div>
          </div>

          <div class="flex gap-4 flex-wrap">
            <a
              href="#"
              class="bg-emerald-500 text-white px-5 py-2 rounded-lg font-medium flex items-center gap-2 hover:bg-emerald-600 transition"
            >
              Register Now <ExternalLink />
            </a>
            <button
              @click="modelOpened"
              class="bg-gray-100 text-gray-800 px-5 py-2 rounded-lg font-medium hover:bg-gray-200 transition"
            >
              View More
            </button>
            <!-- Modal -->
            <Transition name="fade">
              <div
                v-if="isModelopen"
                class="fixed inset-0 bg-black/50 backdrop-blur-sm flex items-center justify-center z-50"
                @click.self="modelClosed"
              >
                <Transition name="scale">
                  <div
                    v-if="isModelopen"
                    class="bg-white rounded-2xl shadow-2xl max-w-2xl w-full p-6 relative transform"
                  >
                    <!-- Modal Content -->
                    <h2 class="text-2xl font-bold mb-4">{{ upcomingEvents[0].title }}</h2>
                    <p class="text-gray-700 mb-4">{{ upcomingEvents[0].moreinfo }}</p>
                  </div>
                </Transition>
              </div>
            </Transition>
          </div>
        </div>
      </div>

      <!-- More Upcoming Events -->
      <div>
        <h3 class="text-2xl font-bold text-gray-900 mb-8 animate-fadeInUp">More Upcoming Events</h3>
        <div class="grid md:grid-cols-2 gap-8">
          <div
            v-for="(event, index) in upcomingEvents.slice(1)"
            :key="event.id"
            class="bg-white/90 backdrop-blur-lg rounded-xl overflow-hidden border border-white/40 shadow-md hover:shadow-lg hover:-translate-y-1 transition p-4 animate-fadeInUp"
          >
            <div class="relative h-52 mb-4">
              <img
                :src="event.image"
                :alt="event.title"
                class="w-full h-full object-cover rounded-lg"
              />
              <div
                class="absolute top-3 left-3 bg-black/70 text-white text-xs px-3 py-1 rounded-full"
              >
                {{ event.type }}
              </div>
            </div>

            <h4 class="text-lg font-semibold text-gray-800 mb-2">{{ event.title }}</h4>
            <p class="text-sm text-gray-600 mb-4">{{ event.description }}</p>

            <div class="flex justify-between items-center text-gray-500 text-xs mb-4">
              <div class="flex items-center gap-1">
                <Calendar />
                {{
                  new Date(event.date).toLocaleDateString('en-US', {
                    month: 'short',
                    day: 'numeric',
                  })
                }}
              </div>
              <div class="flex items-center gap-1"><Users /> {{ event.attendees }}</div>
            </div>

            <a
              href="#"
              class="bg-emerald-500 text-white px-4 py-2 rounded-md text-sm font-medium hover:bg-emerald-600 transition"
              >Register</a
            >
          </div>
        </div>
      </div>

      <!-- Past Events -->
      <div class="mt-16 bg-gray-50/80 border border-gray-200 rounded-xl p-8 animate-fadeInUp">
        <h3 class="text-2xl font-bold text-gray-900 mb-6">Recent Past Events</h3>
        <div class="space-y-4">
          <div
            v-for="event in pastEvents"
            :key="event.title"
            class="flex justify-between items-center bg-white rounded-lg border border-gray-200 p-4"
          >
            <div>
              <h4 class="text-base font-semibold text-gray-800">{{ event.title }}</h4>
              <p class="text-sm text-gray-600">
                {{
                  new Date(event.date).toLocaleDateString('en-US', {
                    month: 'long',
                    day: 'numeric',
                    year: 'numeric',
                  })
                }}
              </p>
            </div>
            <div class="flex items-center gap-6">
              <div class="flex items-center gap-1 text-gray-600 text-sm">
                <Users /> {{ event.attendees }}
              </div>
              <div class="flex items-center gap-2 text-yellow-500 text-sm font-semibold">
                {{ event.rating }} <span>★★★★★</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
<style scoped>
/* Fade for background overlay */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* Scale for modal box */
.scale-enter-active,
.scale-leave-active {
  transition: all 0.3s ease;
}
.scale-enter-from {
  opacity: 0;
  transform: scale(0.9);
}
.scale-leave-to {
  opacity: 0;
  transform: scale(0.9);
}
</style>
