<template>
  <header class="sticky top-0 z-40 bg-sky-900 backdrop-blur-md border-b border-neutral-800">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
      <!-- Logo & Identity -->
      <a href="https://kkpcag.vercel.app/" class="flex items-center space-x-3 group">
        <div class="w-11 h-11 rounded-xl bg-gradient-to-br from-amber-500 via-amber-600 to-amber-700 flex items-center justify-center text-neutral-950 font-extrabold text-xl shadow-lg shadow-amber-500/20">
          <img src="https://www.agghana.org/_nuxt/logo.TuZ7AZUr.png" alt="AG" class="w-6 h-6" />
        </div>
        <div>
          <span class="block text-lg font-bold tracking-tight text-white group-hover:text-amber-400 transition-colors">
            KKPC A/G
          </span>
          <span class="block text-xs uppercase tracking-widest text-amber-500 font-medium">
            Kingdom Keys Prayer   <button @click="$emit('navigate', 'events')" class="hover:text-amber-400 transition-colors"></button> Chapel <br class="hidden sm:inline" /> Assemblies of God church
          </span>
        </div>
      </a>

      <!-- Desktop Nav -->
      <nav class="hidden md:flex items-center space-x-6 text-sm font-medium text-neutral-300 cursor-pointer">
        <button @click="$emit('navigate', 'home')" class="hover:text-amber-400 transition-colors">Home</button>
        <button @click="$emit('navigate', 'devotional')" class="hover:text-amber-400 transition-colors">Living Word</button>
        <button @click="$emit('navigate', 'sermons')" class="hover:text-amber-400 transition-colors">Sermons</button>
        <button @click="$emit('navigate', 'central-aid')" class="hover:text-amber-400 transition-colors">KKPC Aid</button>
        <button @click="$emit('navigate', 'branches')" class="hover:text-amber-400 transition-colors">Locate Church</button>
        <button @click="$emit('navigate', 'events')" class="hover:text-amber-400 transition-colors">Events</button>
          <button @click="$emit('navigate', 'about')" class="hover:text-amber-400 transition-colors">About</button>
      </nav>

      <!-- Action Buttons -->
      <div class="hidden sm:flex items-center space-x-3">
        <button 
          @click="$emit('open-prayer')"
          class="px-4 py-2 text-xs font-semibold rounded-lg border border-neutral-700 text-neutral-200 hover:bg-neutral-800 transition-all"
        >
          Prayer Request
        </button>
        <button 
          @click="$emit('open-give')"
          class="px-5 py-2.5 text-xs font-bold uppercase tracking-wider rounded-lg bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-400 hover:to-amber-500 text-neutral-950 shadow-md shadow-amber-500/20 transition-all transform active:scale-95"
        >
          Give Online
        </button>
      </div>

      <!-- Mobile Menu Toggle -->
      <button 
        @click="mobileOpen = !mobileOpen" 
        class="md:hidden p-2 text-neutral-400 hover:text-white"
        aria-label="Toggle Navigation"
      >
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path v-if="!mobileOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
          <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </div>

    <!-- Mobile Drawer -->
    <div v-if="mobileOpen" class="md:hidden bg-neutral-900 border-b border-neutral-800 px-4 py-6 space-y-4">
      <div class="flex flex-col space-y-3 text-base font-medium">
        <button @click="navClick('home')" class="text-left text-neutral-200 hover:text-amber-400 py-1">Home</button>
        <button @click="navClick('devotional')" class="text-left text-neutral-200 hover:text-amber-400 py-1">Living Word Devotional</button>
        <button @click="navClick('sermons')" class="text-left text-neutral-200 hover:text-amber-400 py-1">Sermons & Media</button>
        <button @click="navClick('central-aid')" class="text-left text-neutral-200 hover:text-amber-400 py-1">KKPC A/G Outreach</button>
        <button @click="navClick('branches')" class="text-left text-neutral-200 hover:text-amber-400 py-1">Locate a Temple</button>
        <button @click="navClick('events')" class="text-left text-neutral-200 hover:text-amber-400 py-1">Conferences & Events</button>
        <button @click="navClick('about')" class="text-left text-neutral-200 hover:text-amber-400 py-1">About</button>
      </div>
      <div class="pt-4 border-t border-neutral-800 flex flex-col space-y-2">
        <button @click="$emit('open-give'); mobileOpen = false" class="w-full py-3 text-center font-bold bg-amber-500 text-neutral-950 rounded-xl">
          Give Online (Tithes & Offering)
        </button>
        <button @click="$emit('open-prayer'); mobileOpen = false" class="w-full py-2.5 text-center font-medium border border-neutral-700 text-white rounded-xl">
          Submit Prayer Request
        </button>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['navigate', 'open-give', 'open-prayer'])
const mobileOpen = ref(false)

const navClick = (id) => {
  emit('navigate', id)
  mobileOpen.value = false
}
</script>