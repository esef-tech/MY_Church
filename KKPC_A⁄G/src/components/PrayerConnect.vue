<template>
  <div class="space-y-5">
    <div>
      <p class="text-xs uppercase tracking-[0.22em] text-amber-500 font-bold">Prayer request</p>
      <h3 class="mt-2 text-2xl font-bold text-white">We are standing with you in prayer</h3>
    </div>

    <form class="space-y-4" @submit.prevent>
      <div>
        <label class="mb-2 block text-sm text-neutral-300">Full name</label>
        <input class="w-full rounded-xl border border-neutral-700 bg-neutral-800 px-4 py-3 text-white outline-none focus:border-amber-500" placeholder="Your name" />
      </div>
      <div>
        <label class="mb-2 block text-sm text-neutral-300">Prayer request</label>
        <textarea rows="4" class="w-full rounded-xl border border-neutral-700 bg-neutral-800 px-4 py-3 text-white outline-none focus:border-amber-500" placeholder="Share your request..."></textarea>
      </div>
      <button type="submit" class="w-full rounded-xl bg-amber-500 px-4 py-3 text-sm font-bold text-neutral-950 hover:bg-amber-400">
        Submit Request
      </button>
    </form>
  </div>
</template>

<script setup>
defineEmits(['close'])
</script>
