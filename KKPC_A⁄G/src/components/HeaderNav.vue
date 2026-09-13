<script setup>
import { ref } from 'vue'

// Contact details
const phoneNumber = '+1 646-294-6127'          // display format
const phoneNumberTel = '+16462946127'          // tel: format (no spaces/symbols)
const email = 'kkprayerchapel@gmail.com'

// Social media links (replace URLs with the website's actual pages)
const socials = [
  { name: 'Facebook',  url: 'https://www.facebook.com/yourpage',   key: 'facebook' },
  { name: 'WhatsApp',  url: 'https://wa.me/16462946127',           key: 'whatsapp' },
  { name: 'YouTube',   url: 'https://www.youtube.com/@yourchannel', key: 'youtube' },
  { name: 'Instagram', url: 'https://www.instagram.com/yourpage',  key: 'instagram' },
  { name: 'TikTok',    url: 'https://www.tiktok.com/@yourpage',    key: 'tiktok' },
]

// Navigation links
// - `type: 'page'`  → standalone page (About, Contact) — emits navigate event
// - `type: 'section'` → in-page scroll via ID selector (everything else)
const navLinks = ref([
  { label: 'Home',       target: 'home',       type: 'page' },
  { label: 'Sermons',    target: 'sermons',    type: 'section' },
  { label: 'Events',     target: 'events',     type: 'section' },
  { label: 'Branches',   target: 'branches',   type: 'section' },
  { label: 'Giving',     target: 'giving',     type: 'section' },
  { label: 'Devotional', target: 'devotional', type: 'section' },
    { label: 'Contact',    target: 'contact',    type: 'page' },
   { label: 'About',      target: 'about',      type: 'page' },
])

const mobileMenuOpen = ref(false)
const toggleMobileMenu = () => (mobileMenuOpen.value = !mobileMenuOpen.value)

// Central navigation handler
// - 'page' links emit a navigate event (App.vue handles page swap)
// - 'section' links also emit navigate; App.vue will switch to home (if needed) and scroll
const handleNavClick = (link) => {
  mobileMenuOpen.value = false
  // Emit the navigate event with the target id; App.vue decides what to do
  // (page swap for 'about'/'contact', in-page scroll for everything else)
  // Use the link's target directly — App.vue already routes 'about' as a page.
  // We also emit 'contact' so App.vue can swap to the contact page.
  // For 'home' and section ids, App.vue will handle accordingly.
  // Emit the navigate event with the link object so the parent has full context
}
</script>

<template>
  <nav class="w-full bg-sky-900 text-white shadow-md">
    <!-- Top utility bar: socials (left) + contact (right) -->
    <div class="max-w-7xl mx-auto px-4 py-2 flex items-center justify-between">
      <!-- LEFT: Social Media Links -->
      <div class="flex items-center gap-3">
        <a
          v-for="social in socials"
          :key="social.key"
          :href="social.url"
          target="_blank"
          rel="noopener noreferrer"
          :aria-label="social.name"
          class="text-gray-300 hover:text-white hover:scale-110 transition-all duration-200"
        >
          <!-- Facebook -->
          <svg v-if="social.key === 'facebook'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-4 h-4">
            <path d="M22 12.06C22 6.5 17.52 2 12 2S2 6.5 2 12.06c0 5 3.66 9.15 8.44 9.94v-7.03H7.9v-2.91h2.54V9.85c0-2.51 1.49-3.9 3.78-3.9 1.09 0 2.23.2 2.23.2v2.46h-1.26c-1.24 0-1.63.77-1.63 1.56v1.87h2.78l-.44 2.91h-2.34V22c4.78-.79 8.44-4.94 8.44-9.94z"/>
          </svg>
          <!-- WhatsApp -->
          <svg v-else-if="social.key === 'whatsapp'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-4 h-4">
            <path d="M.057 24l1.687-6.163a11.867 11.867 0 01-1.587-5.946C.16 5.335 5.495 0 12.05 0a11.82 11.82 0 018.413 3.488 11.82 11.82 0 013.48 8.414c-.003 6.557-5.338 11.892-11.893 11.892a11.9 11.9 0 01-5.688-1.448L.057 24zm6.597-3.807c1.676.995 3.276 1.591 5.392 1.592 5.448 0 9.886-4.434 9.889-9.885.002-5.462-4.415-9.89-9.881-9.892-5.452 0-9.887 4.434-9.889 9.884a9.86 9.86 0 001.51 5.26l-.999 3.648 3.978-1.607zm11.387-5.464c-.074-.124-.272-.198-.57-.347-.297-.149-1.758-.868-2.031-.967-.272-.099-.47-.149-.669.149-.198.297-.768.967-.941 1.165-.173.198-.347.223-.644.074-.297-.149-1.255-.462-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.297-.347.446-.521.151-.172.2-.296.3-.495.099-.198.05-.372-.025-.521-.075-.148-.669-1.611-.916-2.206-.242-.579-.487-.501-.669-.51l-.57-.01c-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.71.306 1.263.489 1.694.626.712.226 1.36.194 1.872.118.571-.085 1.758-.719 2.006-1.413.248-.695.248-1.29.173-1.414z"/>
          </svg>
          <!-- YouTube -->
          <svg v-else-if="social.key === 'youtube'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-4 h-4">
            <path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/>
          </svg>
          <!-- Instagram -->
          <svg v-else-if="social.key === 'instagram'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-4 h-4">
            <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163C8.741 0 8.332.014 7.052.072 2.695.272.273 2.69.073 7.052.014 8.332 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.332 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.668-.072-4.948-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 1 0 0 12.324 6.162 6.162 0 0 0 0-12.324zM12 16a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm6.406-11.845a1.44 1.44 0 1 0 0 2.881 1.44 1.44 0 0 0 0-2.881z"/>
          </svg>
          <!-- TikTok -->
          <svg v-else-if="social.key === 'tiktok'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-4 h-4">
            <path d="M12.525.02c1.31-.02 2.61-.01 3.91-.02.08 1.53.63 3.09 1.75 4.17 1.12 1.11 2.7 1.62 4.24 1.79v4.03c-1.44-.05-2.89-.35-4.2-.97-.57-.26-1.1-.59-1.62-.93-.01 2.92.01 5.84-.02 8.75-.08 1.4-.54 2.79-1.35 3.94-1.31 1.92-3.58 3.17-5.91 3.2-1.43.08-2.86-.31-4.08-1.03-2.02-1.19-3.44-3.37-3.57-5.72-.01-.37-.01-.74.01-1.11.16-2.06 1.27-4.01 2.95-5.19 1.45-1.04 3.29-1.5 5.07-1.21.02 1.48-.01 2.96.01 4.44-.82-.27-1.76-.18-2.49.33-.79.53-1.27 1.46-1.21 2.4.03 1.18.99 2.21 2.16 2.39.96.16 1.99-.34 2.51-1.17.16-.28.27-.59.27-.91.06-1.53.01-3.06.03-4.59.01-3.55-.01-7.1.02-10.65z"/>
          </svg>
        </a>
      </div>

      <!-- RIGHT: Phone & Email (click to call / email) -->
      <div class="flex items-center gap-4 text-sm">
        <!-- Click to call -->
        <a
          :href="`tel:${phoneNumberTel}`"
          class="flex items-center gap-2 text-gray-300 hover:text-white transition-colors duration-200"
          :aria-label="`Call us at ${phoneNumber}`"
        >
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-4 h-4">
            <path d="M6.62 10.79a15.05 15.05 0 0 0 6.59 6.59l2.2-2.2a1 1 0 0 1 1.02-.24c1.12.37 2.33.57 3.57.57a1 1 0 0 1 1 1V20a1 1 0 0 1-1 1A17 17 0 0 1 3 4a1 1 0 0 1 1-1h3.5a1 1 0 0 1 1 1c0 1.24.2 2.45.57 3.57a1 1 0 0 1-.25 1.02l-2.2 2.2z"/>
          </svg>
          <span class="hidden sm:inline">{{ phoneNumber }}</span>
        </a>

        <!-- Click to email -->
        <a
          :href="`mailto:${email}`"
          class="flex items-center gap-2 text-gray-300 hover:text-white transition-colors duration-200"
          :aria-label="`Email us at ${email}`"
        >
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-4 h-4">
            <path d="M20 4H4a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V6a2 2 0 0 0-2-2zm0 4-8 5-8-5V6l8 5 8-5v2z"/>
          </svg>
          <span class="hidden md:inline">{{ email }}</span>
        </a>
      </div>
    </div>

    <!-- Main navbar: brand + nav links -->
    <div class="border-t border-gray-800">
      <div class="max-w-7xl mx-auto px-4 py-3 flex items-center justify-between">
        <!-- Brand -->
        <a href="https://kkpcag.vercel.app/" class="flex items-center space-x-3 group">
          <div class="w-11 h-11 rounded-xl bg-gradient-to-br from-amber-500 via-amber-600 to-amber-700 flex items-center justify-center text-neutral-950 font-extrabold text-xl shadow-lg shadow-amber-500/20">
            <img src="https://www.agghana.org/_nuxt/logo.TuZ7AZUr.png" alt="AG" class="w-6 h-6" />
          </div>
          <div>
            <span class="block text-lg font-bold tracking-tight text-white group-hover:text-amber-400 transition-colors">
              KKPC A/G
            </span>
            <span class="block text-xs uppercase tracking-widest text-amber-500 font-medium">
              Kingdom Keys Prayer Chapel <br class="hidden sm:inline" /> Assemblies of God church
            </span>
          </div>
        </a>

        <!-- Desktop nav links -->
        <ul class="hidden md:flex items-center gap-6 text-sm font-medium">
          <li v-for="link in navLinks" :key="link.label">
            <!--
              All nav links emit a 'navigate' event with the target id.
              - 'about' and 'contact' → standalone pages
              - everything else → in-page section scroll on home
              App.vue's handleNavigate decides what to do based on the id.
            -->
            <button
              type="button"
              class="text-gray-300 hover:text-amber-400 transition-colors duration-200"
              @click="$emit('navigate', link.target)"
            >
              {{ link.label }}
            </button>
          </li>
        </ul>

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

        <!-- Mobile menu toggle -->
        <button
          class="md:hidden text-gray-200 hover:text-white"
          @click="toggleMobileMenu"
          aria-label="Toggle menu"
        >
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="w-6 h-6">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
          </svg>
        </button>
      </div>

      <!-- Mobile dropdown -->
      <div v-if="mobileMenuOpen" class="md:hidden bg-gray-900 border-t border-gray-800">
        <ul class="flex flex-col px-4 py-3 gap-3 text-sm">
          <li v-for="link in navLinks" :key="link.label">
            <!--
              Mobile links also emit 'navigate' with the target id.
              The toggleMobileMenu call closes the dropdown after click.
            -->
            <button
              type="button"
              class="block w-full text-left text-gray-300 hover:text-amber-400 transition-colors"
              @click="mobileMenuOpen = false; $emit('navigate', link.target)"
            >
              {{ link.label }}
            </button>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>