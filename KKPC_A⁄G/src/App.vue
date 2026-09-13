<template>
  <div class="min-h-screen bg-[#0b0f19] text-neutral-100 flex flex-col selection:bg-amber-500 selection:text-neutral-950">
    <!-- Navigation Bar -->
    <HeaderNav
      :active-section="activeSection"
      @navigate="handleNavigate"
      @open-give="showGiveModal = true"
      @open-prayer="showPrayerModal = true"
    />

    <main class="flex-1">
      <!-- About — rendered as its own standalone page -->
      <About
        v-if="currentPage === 'about'"
        id="about"
        @navigate="handleNavigate"
        @open-give="showGiveModal = true"
        @open-prayer="showPrayerModal = true"
      />

      <!-- Contact — rendered as its own standalone page -->
      <Contact        v-else-if="currentPage === 'contact'"
        id="contact"
        @navigate="handleNavigate"
        @open-give="showGiveModal = true"
        @open-prayer="showPrayerModal = true"
      />

      <!-- Home page content -->
      <template v-else>
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
      </template>
    </main>

    <!-- Footer -->
    <FooterSection
      @navigate="handleNavigate"
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
import { ref, nextTick } from 'vue'
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
import About from './components/About.vue'
import Contact from  './components/Contact.vue'

const activeSection = ref('home')
// 'home' | 'about' | 'contact'
const currentPage = ref('home')
const showGiveModal = ref(false)
const showPrayerModal = ref(false)

const scrollToSection = (id) => {
  activeSection.value = id
  const el = document.getElementById(id)
  if (el) {
    el.scrollIntoView({ behavior: 'smooth' })
  }
}

// Central navigation handler.
// - 'about' and 'contact' → standalone pages (swap currentPage)
// - 'home' → go back to home (top of page)
// - section ids (devotional, sermons, giving, branches, events) → in-page scroll,
//   switching back to home first if currently on About or Contact page
const handleNavigate = (id) => {
  // About — standalone page
  if (id === 'about') {
    currentPage.value = 'about'
    activeSection.value = 'about'
    window.scrollTo({ top: 0, behavior: 'smooth' })
    return
  }

  // Contact — standalone page
  if (id === 'contact') {
    currentPage.value = 'contact'
    activeSection.value = 'contact'
    window.scrollTo({ top: 0, behavior: 'smooth' })
    return
  }

  // Home — go back to home page (top)
  if (id === 'home') {
    currentPage.value = 'home'
    activeSection.value = 'home'
    window.scrollTo({ top: 0, behavior: 'smooth' })
    return
  }

  // Section ids — need to be on the home page first, then scroll
  if (currentPage.value !== 'home') {
    currentPage.value = 'home'
    activeSection.value = id
    nextTick(() => {
      // wait for home sections to mount before scrolling
      setTimeout(() => scrollToSection(id), 50)
    })
    return
  }

  // Already on home — just scroll to the section
  scrollToSection(id)
}
</script>