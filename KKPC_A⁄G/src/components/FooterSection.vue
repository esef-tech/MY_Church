<template>
  <footer class="border-t border-neutral-800 bg-[#0f172a] py-12">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex flex-col gap-8 lg:flex-row lg:items-center lg:justify-between">
        <div>
          <div class="flex items-center space-x-3">
            <div class="flex h-11 w-11 items-center justify-center rounded-xl bg-gradient-to-br from-amber-500 via-amber-600 to-amber-700 text-lg font-black text-neutral-950">
              <img src="https://www.agghana.org/_nuxt/logo.TuZ7AZUr.png" alt="AG" class="w-6 h-6" />
            </div>
            <div>
              <div class="text-lg font-bold text-white">KKPC A/G</div>
              <div class="text-[10px] uppercase tracking-[0.22em] text-amber-500"> Kingdom Keys Prayer Chapel <br class="hidden sm:inline" /> Assemblies of God church</div>
            </div>
          </div>
          <p class="mt-4 max-w-md text-sm text-neutral-400">
            A place of worship, discipleship, prayer, and community impact across the nations.
          </p>
        </div>

        <div class="flex flex-wrap gap-4 text-sm text-neutral-300">
          <button @click="$emit('navigate', 'devotional')" class="hover:text-amber-400">Living Word</button>
          <button @click="$emit('navigate', 'sermons')" class="hover:text-amber-400">Sermons</button>
          <button @click="$emit('navigate', 'giving')" class="hover:text-amber-400">Giving</button>
          <button @click="$emit('navigate', 'branches')" class="hover:text-amber-400">Branches</button>
        </div>

        <div class="flex gap-3">
          <button @click="$emit('open-give')" class="rounded-xl bg-amber-500 px-4 py-2 text-sm font-bold text-neutral-950 hover:bg-amber-400">Give Online</button>
          <button @click="$emit('open-prayer')" class="rounded-xl border border-neutral-700 px-4 py-2 text-sm font-bold text-white hover:border-amber-500 hover:text-amber-400">Prayer</button>
        </div>
      </div>

      <div class="mt-8 border-t border-neutral-800 pt-6 text-center text-xs text-neutral-500">
        © 2026 KKPC A/G Kingdom Keys Prayer Chapel Assemblies of God Church. All rights reserved.
      </div>
    </div>
  </footer>
</template>

<script setup>
defineEmits(['navigate', 'open-give', 'open-prayer'])
</script>
