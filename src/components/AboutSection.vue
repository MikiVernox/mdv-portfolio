<template>
  <section id="about" class="py-24 bg-zinc-950 border-t border-zinc-800">
    <!-- Section Label -->
    <div class="max-w-7xl mx-auto px-6">
      <div class="flex items-center gap-4 mb-16">
        <span class="font-mono text-xs text-pink-500 uppercase tracking-widest">01 — ABOUT</span>
        <div class="h-px flex-1 bg-zinc-800"></div>
      </div>
    </div>

    <div class="max-w-7xl mx-auto px-6 grid grid-cols-1 lg:grid-cols-3 gap-12">
      <!-- Col span-2: Bio -->
      <div class="lg:col-span-2">
        <p class="font-mono text-zinc-300 text-sm leading-relaxed">
          {{ data.profile.intro }}
        </p>
        <p class="font-mono text-zinc-300 text-sm leading-relaxed mt-6">
          {{ data.profile.bio }}
        </p>
        
        <div class="font-mono text-xs text-zinc-500 mt-6">
          &gt;&gt; PRONOUNS: {{ data.profile.pronouns }} | LOCATION: {{ data.profile.location }}
        </div>

        <div class="flex flex-wrap gap-4 mt-8">
          <a :href="data.profile.social.github" target="_blank" class="font-mono text-xs border border-zinc-700 px-3 py-2 hover:border-pink-500 hover:text-pink-400 transition-all duration-200">
            GH ↗
          </a>
          <a :href="data.profile.social.linkedin" target="_blank" class="font-mono text-xs border border-zinc-700 px-3 py-2 hover:border-pink-500 hover:text-pink-400 transition-all duration-200">
            LI ↗
          </a>
          <a :href="data.profile.social.instagram" target="_blank" class="font-mono text-xs border border-zinc-700 px-3 py-2 hover:border-pink-500 hover:text-pink-400 transition-all duration-200">
            IG ↗
          </a>
        </div>
      </div>

      <!-- Col span-1: Skills Panel -->
      <div class="lg:col-span-1">
        <div class="border border-zinc-800 bg-zinc-900 p-6">
          <div v-for="(list, category) in data.profile.skills" :key="category" class="mb-6 last:mb-0">
            <div class="font-mono text-xs text-zinc-600 uppercase tracking-widest mb-3">
              {{ category }}
            </div>
            <div class="flex flex-wrap">
              <span 
                v-for="skill in list" 
                :key="skill"
                class="inline-block border border-zinc-700 font-mono text-xs text-zinc-400 px-3 py-1 m-1 hover:border-pink-500 hover:text-pink-400 transition-all duration-200"
              >
                {{ skill }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import data from '../data/portfolioData'
</script>
