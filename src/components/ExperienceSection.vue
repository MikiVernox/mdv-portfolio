<template>
  <section id="experience" class="py-24 bg-zinc-950 border-t border-zinc-800">
    <!-- Section Label -->
    <div class="max-w-7xl mx-auto px-6">
      <div class="flex items-center gap-4 mb-16">
        <span class="font-mono text-xs text-pink-500 uppercase tracking-widest">03 — EXPERIENCE</span>
        <div class="h-px flex-1 bg-zinc-800"></div>
      </div>
    </div>

    <div class="max-w-7xl mx-auto px-6">
      <div class="min-h-[300px] border-l border-zinc-800 pl-8 ml-3">
        <div class="flex items-center gap-2">
          <div class="w-2 h-2 bg-pink-500 rounded-full -ml-9 mt-1.5 flex-shrink-0"></div>
          <div class="font-mono text-white font-bold">{{ data.experience[0].role }}</div>
        </div>
        <div class="font-mono text-purple-400 text-sm mt-1">{{ data.experience[0].company }}</div>
        <div class="font-mono text-xs text-zinc-600 mt-1">{{ data.experience[0].period }} • {{ data.experience[0].location }}</div>
        <p class="font-mono text-zinc-400 text-sm leading-relaxed mt-3 max-w-2xl">
          {{ data.experience[0].description }}
        </p>
      </div>
    </div>
  </section>
</template>

<script setup>
import data from '../data/portfolioData'
</script>
