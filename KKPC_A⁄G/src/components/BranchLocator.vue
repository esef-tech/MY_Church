<template>
  <section class="bg-neutral-950 py-20">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="mb-12 text-center">
        <span class="text-xs uppercase tracking-[0.22em] text-amber-500 font-bold">Find a branch</span>
        <h2 class="mt-3 text-3xl sm:text-4xl font-bold text-white">Locate our church family</h2>
      </div>

      <div class="grid gap-5 md:grid-cols-2 lg:grid-cols-3">
        <div v-for="branch in branches" :key="branch.city" class="rounded-2xl border border-neutral-800 bg-neutral-900 p-5">
          <h3 class="text-xl font-bold text-white">{{ branch.city }}</h3>
          <p class="mt-2 text-sm text-neutral-400">{{ branch.address }}</p>
          <div class="mt-4 text-sm text-amber-400 font-medium">{{ branch.service }}</div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const branches = [
  { city: 'Accra', address: 'ICGC Christ Temple', service: 'Sunday • 7:00 AM / 9:30 AM' },
  { city: 'Kumasi', address: 'ICGC Temple', service: 'Sunday • 8:00 AM / 10:00 AM' },
  { city: 'London', address: 'ICGC London', service: 'Sunday • 9:00 AM / 11:00 AM' },
  { city: 'New York', address: 'ICGC New York', service: 'Sunday • 9:30 AM / 11:30 AM' },
  { city: 'Cape Town', address: 'ICGC Cape Town', service: 'Sunday • 8:30 AM / 10:30 AM' },
  { city: 'Nairobi', address: 'ICGC Nairobi', service: 'Sunday • 9:00 AM / 11:00 AM' }
]
</script>
