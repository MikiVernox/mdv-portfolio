<template>
  <section id="experience" class="py-24 bg-zinc-950 border-t border-zinc-800">
    <!-- Section Label -->
    <div class="max-w-7xl mx-auto px-6">
      <div class="flex items-center gap-4 mb-16">
        <span class="font-mono text-xs text-pink-500 uppercase tracking-widest">03 — LEVEL</span>
        <div class="h-px flex-1 bg-zinc-800"></div>
      </div>
    </div>

    <div class="max-w-7xl mx-auto px-6">
      <div class="mb-12">
        <div class="font-mono text-5xl font-black text-white uppercase tracking-tighter">
          Junior
        </div>
        <div class="font-mono text-zinc-500 text-sm mt-2 uppercase tracking-widest">
          Game Developer
        </div>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
        <div v-for="exp in data.experience" :key="exp.id" class="border-l border-zinc-800 pl-8 ml-3">
          <div class="flex items-center gap-2">
            <div class="w-2 h-2 bg-pink-500 rounded-full -ml-9 mt-1.5 flex-shrink-0"></div>
            <div class="font-mono text-white font-bold">{{ exp.role }}</div>
          </div>
          <div class="font-mono text-purple-400 text-sm mt-1">{{ exp.company }}</div>
          <div class="font-mono text-xs text-zinc-600 mt-1">{{ exp.period }} • {{ exp.location }}</div>
          <p class="font-mono text-zinc-400 text-sm leading-relaxed mt-3 max-w-2xl">
            {{ exp.description }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import data from '../data/portfolioData'
</script>
