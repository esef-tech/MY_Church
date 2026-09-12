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
  { city: 'Tucson', address: '3275 N Swan Rd, Tucson, AZ 85712', service: 'Sunday • 7:00 AM / 9:30 AM' },
  { city: 'Phoenix', address: '1440 E Northern Ave, Phoenix, AZ 85020', service: 'Sunday • 8:00 AM / 10:00 AM' },
  { city: 'Flagstaff', address: '1900 N Fort Valley Rd, Flagstaff, AZ 86001', service: 'Sunday • 9:00 AM / 11:00 AM' },
  { city: 'Glendale', address: '7550 W Bethany Home Rd, Glendale, AZ 85303', service: 'Sunday • 9:30 AM / 11:30 AM' },
  { city: 'Mesa', address: '2100 S Power Rd, Mesa, AZ 85209', service: 'Sunday • 8:30 AM / 10:30 AM' },
  { city: 'Tempe', address: '815 E University Dr, Tempe, AZ 85281', service: 'Sunday • 9:00 AM / 11:00 AM' }
]
</script>
