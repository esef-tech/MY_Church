<template>
  <section class="py-20 bg-[#0f172a] border-y border-neutral-800/80">
    <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center max-w-2xl mx-auto mb-12">
        <span class="text-xs uppercase tracking-widest text-amber-500 font-bold">Daily Inspiration</span>
        <h2 class="text-3xl sm:text-4xl font-bold text-white mt-2">Living Word Devotional</h2>
        <p class="text-neutral-400 text-sm mt-3">Spiritual nourishment and pastoral wisdom for daily victory by Pastor William Abaidoo.</p>
      </div>

      <!-- Devotional Card -->
      <div class="bg-neutral-900 border border-neutral-800 rounded-3xl p-6 sm:p-10 shadOpen file in editor (ctrl + click)

ow-2xl relative overflow-hidden">
        <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 border-b border-neutral-800 pb-6 mb-6">
          <div>
            <span class="inline-block text-xs font-semibold px-3 py-1 rounded-full bg-amber-500/10 text-amber-400 border border-amber-500/20 mb-2">
              Today's Devotional • Sept 13
            </span>
            <h3 class="text-2xl font-bold text-white">Standing Firm in the Promise</h3>
            <p class="text-sm text-neutral-400 mt-1">Scripture: <span class="text-amber-400 font-semibold">Hebrews 10:23</span></p>
          </div>

          <!-- Audio Player Pill -->
          <div class="flex items-center gap-3 bg-neutral-800/80 border border-neutral-700/60 px-4 py-2 rounded-2xl">
            <button 
              @click="toggleAudio"
              class="w-9 h-9 rounded-full bg-amber-500 text-neutral-950 flex items-center justify-center font-bold"
            >
              {{ isPlaying ? '⏸' : '▶' }}
            </button>
            <div class="text-xs">
              <span class="block font-semibold text-white">Listen to Audio</span>
              <span class="text-neutral-400">Pastor William Abaidoo (6:45)</span>
            </div>
          </div>
        </div>

        <!-- Scripture Quote -->
        <blockquote class="border-l-4 border-amber-500 pl-4 italic text-neutral-300 text-base mb-6 bg-amber-500/5 p-4 rounded-r-xl">
          "Let us hold fast the confession of our hope without wavering, for He who promised is faithful."
        </blockquote>

        <!-- Body Content -->
        <div class="space-y-4 text-neutral-300 leading-relaxed text-sm sm:text-base">
          <p>
            Life often tests our resolve and pushes us to question whether God's promises will manifest in our reality. In the midst of contradicting circumstances, the natural instinct is to surrender or to alter our confession. However, the scripture reminds us that our faith is anchored not on shifting human conditions, but on the unchangeable fidelity of God.
          </p>
          <p>
            To hold fast means to grip with unyielding tenacity. When fear whispers uncertainty into your heart, you must choose to voice what God has declared over your health, your home, and your vocation. God's faithfulness is not subject to economic cycles or cultural instability.
          </p>
        </div>

        <!-- Declaration & Prayer -->
        <div class="mt-8 pt-6 border-t border-neutral-800 grid sm:grid-cols-2 gap-6">
          <div class="bg-neutral-800/40 p-5 rounded-2xl border border-neutral-800">
            <h4 class="text-xs uppercase tracking-wider text-amber-400 font-bold mb-2">Daily Confession</h4>
            <p class="text-xs text-neutral-300 italic">
              "I declare that I hold fast to God's promise without wavering. He who called me is faithful, and He will complete the good work He began in me. In Jesus' name, Amen."
            </p>
          </div>
          <div class="bg-neutral-800/40 p-5 rounded-2xl border border-neutral-800">
            <h4 class="text-xs uppercase tracking-wider text-amber-400 font-bold mb-2">Prayer of Faith</h4>
            <p class="text-xs text-neutral-300 italic">
              "Heavenly Father, anchor my heart in Your unfailing truth. Whenever doubts arise, empower me with holy boldness to speak life, hope, and victory over every circumstance. Amen."
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const isPlaying = ref(false)
const toggleAudio = () => {
  isPlaying.value = !isPlaying.value
}
</script>