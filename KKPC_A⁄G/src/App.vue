<template>
  <div class="min-h-screen bg-[#0b0f19] text-neutral-100 flex flex-col selection:bg-amber-500 selection:text-neutral-950">
    <!-- Navigation Bar -->
    <HeaderNav 
      :active-section="activeSection" 
      @navigate="scrollToSection"
      @open-give="showGiveModal = true"
      @open-prayer="showPrayerModal = true"
    />

    <main class="flex-1">
      <!-- Hero / Live Stream section -->
      <HeroStream 
        @open-give="showGiveModal = true"
        @open-prayer="showPrayerModal = true"
      />

      <!-- Living Word Daily Devotional -->
      <LivingWord id="devotional" />

      <!-- Sermons & Media Archive -->
      <SermonsArchive id="sermons" />

      <!-- Online Giving & Tithing Portal -->
      <GivingPortal id="giving" />

      <!-- Central Aid Educational Scholarship Fund -->
      <CentralAid id="central-aid" @open-give="showGiveModal = true" />

      <!-- Global Church & Branch Locator -->
      <BranchLocator id="branches" />

      <!-- Events & Conferences (Greater Works) -->
      <EventsList id="events" />
    </main>

    <!-- Footer -->
    <FooterSection 
      @navigate="scrollToSection"
      @open-give="showGiveModal = true"
      @open-prayer="showPrayerModal = true"
    />

    <!-- Giving Modal Overlay -->
    <div v-if="showGiveModal" class="fixed inset-0 z-50 bg-black/80 backdrop-blur-sm flex items-center justify-center p-4">
      <div class="bg-neutral-900 border border-neutral-800 rounded-2xl max-w-2xl w-full max-h-[90vh] overflow-y-auto p-6 relative">
        <button 
          @click="showGiveModal = false"
          class="absolute top-4 right-4 text-neutral-400 hover:text-white p-2"
        >
          ✕
        </button>
        <GivingPortal :is-modal="true" @completed="showGiveModal = false" />
      </div>
    </div>

    <!-- Prayer Request Modal -->
    <div v-if="showPrayerModal" class="fixed inset-0 z-50 bg-black/80 backdrop-blur-sm flex items-center justify-center p-4">
      <div class="bg-neutral-900 border border-neutral-800 rounded-2xl max-w-lg w-full p-6 relative">
        <button 
          @click="showPrayerModal = false"
          class="absolute top-4 right-4 text-neutral-400 hover:text-white p-2"
        >
          ✕
        </button>
        <PrayerConnect @close="showPrayerModal = false" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import HeaderNav from './components/HeaderNav.vue'
import HeroStream from './components/HeroStream.vue'
import LivingWord from './components/LivingWord.vue'
import SermonsArchive from './components/SermonsArchive.vue'
import GivingPortal from './components/GivingPortal.vue'
import CentralAid from './components/CentralAid.vue'
import BranchLocator from './components/BranchLocator.vue'
import EventsList from './components/EventsList.vue'
import PrayerConnect from './components/PrayerConnect.vue'
import FooterSection from './components/FooterSection.vue'

const activeSection = ref('home')
const showGiveModal = ref(false)
const showPrayerModal = ref(false)

const scrollToSection = (id) => {
  activeSection.value = id
  const el = document.getElementById(id)
  if (el) {
    el.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>