<template>
  <section class="bg-neutral-950 py-20">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-12">
        <span class="text-xs uppercase tracking-[0.22em] text-amber-500 font-bold">Messages & Media</span>
        <h2 class="mt-3 text-3xl sm:text-4xl font-bold text-white">Sermons & Media Archive</h2>
      </div>

      <div class="grid gap-6 md:grid-cols-3">
        <article v-for="sermon in sermons" :key="sermon.title" class="rounded-2xl border border-neutral-800 bg-neutral-900 p-5">
          <div class="mb-4 flex items-center justify-between">
            <span class="rounded-full bg-amber-500/10 px-2.5 py-1 text-[10px] font-bold uppercase tracking-[0.2em] text-amber-400">
              {{ sermon.series }}
            </span>
            <span class="text-xs text-neutral-400">{{ sermon.length }}</span>
          </div>
          <h3 class="text-xl font-bold text-white">{{ sermon.title }}</h3>
          <p class="mt-3 text-sm text-neutral-400">{{ sermon.summary }}</p>
          <button class="mt-5 inline-flex rounded-lg border border-neutral-700 px-3 py-2 text-xs font-semibold text-white transition hover:border-amber-500 hover:text-amber-400">
            Listen now
          </button>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
const sermons = [
  {
    title: 'The Power of Grace',
    series: 'Sunday Message',
    length: '32 min',
    summary: 'A practical teaching on how God’s grace sustains us through every challenge.'
  },
  {
    title: 'Living With Kingdom Vision',
    series: 'Impact Series',
    length: '41 min',
    summary: 'Discover how a kingdom mindset transforms our decisions, relationships, and purpose.'
  },
  {
    title: 'Breaking Spiritual Barriers',
    series: 'Prayer & Revival',
    length: '28 min',
    summary: 'Learn how to walk in authority, prayer, and divine breakthrough every day.'
  }
]
</script>
