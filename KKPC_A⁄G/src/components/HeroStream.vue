<template>
  <section class="relative overflow-hidden bg-gradient-to-br from-neutral-950 via-neutral-900 to-[#111827]">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-20 lg:py-28">
      <div class="grid lg:grid-cols-2 gap-10 items-center">
        <div>
          <span class="inline-flex items-center rounded-full border border-amber-500/30 bg-amber-500/10 px-4 py-2 text-xs font-semibold uppercase tracking-[0.2em] text-amber-400">
            Welcome to Kingdom Keys Prayer Chapel <br> Assemblies of God church <br class="hidden sm:inline" /> 
          </span>
          <h1 class="mt-6 text-4xl sm:text-5xl lg:text-6xl font-black leading-tight text-white">
            Experience <span class="text-amber-400">faith, hope, and renewal</span>
          </h1>
          <p class="mt-6 max-w-xl text-base sm:text-lg text-neutral-300">
            Join the Kingdom Keys Prayer Chapel family in worship, discipleship, and transformative community prayer across Arizona. A family across Arizona pursuing God in worship, discipleship, and transformative prayer.
          </p>

          <div class="mt-8 flex flex-wrap gap-4">
            <button @click="$emit('open-give')" class="rounded-xl bg-amber-500 px-6 py-3 text-sm font-bold text-neutral-950 shadow-lg shadow-amber-500/20 transition hover:bg-amber-400">
              Give Online
            </button>
            <button @click="$emit('open-prayer')" class="rounded-xl border border-neutral-700 bg-neutral-900/60 px-6 py-3 text-sm font-bold text-white transition hover:border-amber-500 hover:text-amber-400">
              Prayer Request
            </button>
          </div>

          <div class="mt-10 flex flex-wrap gap-6 text-sm text-neutral-300">
            <div>
              <div class="text-2xl font-black text-white">1k+</div>
              <div class="text-neutral-400">Worshippers</div>
            </div>
            <div>
              <div class="text-2xl font-black text-white">24/7</div>
              <div class="text-neutral-400">Prayer support</div>
            </div>
            <div>
              <div class="text-2xl font-black text-white">1</div>
              <div class="text-neutral-400">Locations</div>
            </div>
          </div>
        </div>

        <div class="relative">
          <div class="rounded-[2rem] border border-neutral-800 bg-neutral-900/80 p-4 shadow-2xl shadow-black/30">
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
</script>
