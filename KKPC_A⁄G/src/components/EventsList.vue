<template>
  <section class="bg-neutral-900 py-20">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="mb-12 text-center">
        <span class="text-xs uppercase tracking-[0.22em] text-amber-500 font-bold">Events & Conferences</span>
        <h2 class="mt-3 text-3xl sm:text-4xl font-bold text-white">Greater Works Gatherings</h2>
      </div>

      <div class="grid gap-6 md:grid-cols-3">
        <article v-for="event in events" :key="event.name" class="rounded-2xl border border-neutral-800 bg-neutral-950 p-6">
          <div class="mb-4 inline-flex rounded-full bg-amber-500/10 px-2.5 py-1 text-[10px] font-bold uppercase tracking-[0.2em] text-amber-400">
            {{ event.date }}
          </div>
          <h3 class="text-xl font-bold text-white">{{ event.name }}</h3>
          <p class="mt-3 text-sm text-neutral-400">{{ event.description }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
const events = [
  {
    name: 'Greater Works Conference',
    date: 'Sep 20',
    description: 'A season of powerful teaching, worship, and prayer for spiritual growth.'
  },
  {
    name: 'Women of Purpose',
    date: 'Oct 4',
    description: 'An uplifting gathering focused on faith, destiny, and transformation.'
  },
  {
    name: 'Youth Revival',
    date: 'Nov 15',
    description: 'A vibrant youth gathering designed to ignite passion, purpose, and holiness.'
  }
]
</script>
