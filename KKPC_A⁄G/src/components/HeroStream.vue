<template>
  <section class="relative overflow-hidden">
    <!-- Background image layer (replaces the previous gradient-only background) -->
    <div
      class="absolute inset-0 bg-cover bg-center bg-no-repeat"
      :style="{ backgroundImage: `url('${bgImage}')` }"
      aria-hidden="true"
    ></div>

    <!-- Dark overlay preserves the original neutral/amber theme and keeps text readable -->
    <div
      class="absolute inset-0 bg-gradient-to-br from-neutral-950/90 via-neutral-900/85 to-[#111827]/90"
      aria-hidden="true"
    ></div>
    <div class="absolute inset-0 bg-black/30" aria-hidden="true"></div>

    <!-- Content sits above the background -->
    <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-20 lg:py-28">
      <div class="grid lg:grid-cols-2 gap-10 items-center">
        <div>
          <span class="inline-flex items-center rounded-full border border-amber-500/30 bg-amber-500/10 px-4 py-2 text-xs font-semibold uppercase tracking-[0.2em] text-amber-400 backdrop-blur-sm">
            Welcome to Kingdom Keys Prayer Chapel <br> Assemblies of God church <br class="hidden sm:inline" /> 
          </span>
          <h1 class="mt-6 text-4xl sm:text-5xl lg:text-6xl font-black leading-tight text-white drop-shadow-lg">
            Experience <span class="text-amber-400">faith, hope, and renewal</span>
          </h1>
          <p class="mt-6 max-w-xl text-base sm:text-lg text-neutral-200 drop-shadow">
            Join the Kingdom Keys Prayer Chapel family in worship, discipleship, and transformative community prayer across Arizona. A family across Arizona pursuing God in worship, discipleship, and transformative prayer.
          </p>

          <div class="mt-8 flex flex-wrap gap-4">
            <button @click="$emit('open-give')" class="rounded-xl bg-amber-500 px-6 py-3 text-sm font-bold text-neutral-950 shadow-lg shadow-amber-500/20 transition hover:bg-amber-400">
              Give Online
            </button>
            <button @click="$emit('open-prayer')" class="rounded-xl border border-neutral-700 bg-neutral-900/60 px-6 py-3 text-sm font-bold text-white backdrop-blur-sm transition hover:border-amber-500 hover:text-amber-400">
              Prayer Request
            </button>
          </div>

          <div class="mt-10 flex flex-wrap gap-6 text-sm text-neutral-200">
            <div>
              <div class="text-2xl font-black text-white">1k+</div>
              <div class="text-neutral-300">Worshippers</div>
            </div>
            <div>
              <div class="text-2xl font-black text-white">24/7</div>
              <div class="text-neutral-300">Prayer support</div>
            </div>
            <div>
              <div class="text-2xl font-black text-white">1</div>
              <div class="text-neutral-300">Locations</div>
            </div>
          </div>
        </div>

        <div class="relative">
          <div class="rounded-[2rem] border border-neutral-800 bg-neutral-900/80 p-4 shadow-2xl shadow-black/30 backdrop-blur-md">
            <div class="aspect-video overflow-hidden rounded-[1.5rem] bg-gradient-to-br from-amber-500/20 via-neutral-900 to-neutral-950 p-6">
              <div class="flex h-full flex-col justify-between rounded-[1.25rem] border border-neutral-800 bg-neutral-950/70 p-5">
                <div class="flex items-center justify-between">
                  <span class="text-xs font-semibold uppercase tracking-[0.2em] text-amber-400">Live</span>
                  <span class="rounded-full bg-red-500/20 px-2 py-1 text-[10px] font-bold text-red-300">ON AIR</span>
                </div>
                <div>
                  <p class="text-sm text-neutral-400">Sunday Service</p>
                  <h2 class="mt-2 text-2xl font-bold text-white">The Power of Faith</h2>
                </div>
                <div class="flex items-center justify-between text-sm text-neutral-200">
                  <span>8:00 AM • Tucson, AZ</span>
                  <button class="rounded-full bg-amber-500 px-4 py-2 font-semibold text-neutral-950">Watch</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
defineEmits(['open-give', 'open-prayer'])

/**
 * Background image for the hero section.
 * The original Unsplash link returned a 404 (photo removed),
 * so a matching worship-stage photo was generated and saved to
 * /public/worship/stage-bg.png. Swap this for any URL/path you like,
 * e.g. const bgImage = 'https://images.unsplash.com/photo-XXXXX?...'
 */
const bgImage = 'https://images.unsplash.com/photo-1507692049790-de58290a4334?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8Y2h1cmNoJTIwd29yc2hpcCUyMHZpZGVvfGVufDB8fDB8fHww'
</script>