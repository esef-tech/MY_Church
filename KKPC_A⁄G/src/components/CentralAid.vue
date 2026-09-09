<template>
  <section class="bg-[#0f172a] py-20">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="rounded-3xl border border-neutral-800 bg-neutral-900 p-8 sm:p-12">
        <div class="grid gap-10 lg:grid-cols-2 items-center">
          <div>
            <span class="text-xs uppercase tracking-[0.22em] text-amber-500 font-bold">Central Aid</span>
            <h2 class="mt-4 text-3xl sm:text-4xl font-bold text-white">Educating, empowering, and transforming lives</h2>
            <p class="mt-5 text-neutral-300">
              Central Aid supports students and families through scholarships, educational resources, and practical community care.
            </p>
            <button @click="$emit('open-give')" class="mt-8 rounded-xl bg-amber-500 px-6 py-3 text-sm font-bold text-neutral-950 hover:bg-amber-400">
              Support the Fund
            </button>
          </div>
          <div class="grid gap-4 sm:grid-cols-2">
            <div class="rounded-2xl border border-neutral-800 bg-neutral-950 p-5">
              <div class="text-3xl font-black text-white">52k+</div>
              <div class="mt-2 text-sm text-neutral-400">Students served</div>
            </div>
            <div class="rounded-2xl border border-neutral-800 bg-neutral-950 p-5">
              <div class="text-3xl font-black text-white">18</div>
              <div class="mt-2 text-sm text-neutral-400">Academic programs</div>
            </div>
            <div class="rounded-2xl border border-neutral-800 bg-neutral-950 p-5 sm:col-span-2">
              <div class="text-3xl font-black text-white">Education</div>
              <div class="mt-2 text-sm text-neutral-400">Making quality education accessible to families across Ghana and beyond.</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
defineEmits(['open-give'])
</script>
