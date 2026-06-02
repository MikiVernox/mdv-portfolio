<template>
  <section id="projects" class="py-24 bg-black border-t border-zinc-800">
    <!-- Section Label -->
    <div class="max-w-7xl mx-auto px-6">
      <div class="flex items-center gap-4 mb-16">
        <span class="font-mono text-xs text-pink-500 uppercase tracking-widest">02 — PROJECTS</span>
        <div class="h-px flex-1 bg-zinc-800"></div>
      </div>
    </div>

    <div class="max-w-7xl mx-auto px-6">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-px bg-zinc-800">
        <div 
          v-for="project in data.projects" 
          :key="project.id"
          class="bg-zinc-950 p-6 hover:bg-zinc-900 transition-colors duration-300 group cursor-pointer"
          @click="expandedId = expandedId === project.id ? null : project.id"
        >
          <!-- Engine/type tag -->
          <span class="font-mono text-xs text-purple-400 uppercase tracking-widest">{{ project.type }}</span>

          <!-- Title -->
          <h3 class="font-mono text-white text-lg font-bold mt-3 group-hover:text-pink-400 transition-colors duration-200">
            {{ project.title }}
          </h3>

          <!-- Description -->
          <p class="font-mono text-zinc-500 text-xs leading-relaxed mt-3">{{ project.description }}</p>

          <!-- Tags -->
          <div class="flex flex-wrap gap-2 mt-5">
            <span v-for="tag in project.tags" :key="tag"
              class="font-mono text-xs text-zinc-600 border border-zinc-800 px-2 py-1">
              {{ tag }}
            </span>
          </div>

          <!-- YouTube embed toggle -->
          <div v-if="expandedId === project.id" class="mt-4 aspect-video">
            <iframe
              class="w-full h-full"
              :src="`https://www.youtube.com/embed/${project.videoId}?autoplay=1&mute=1&loop=1&playlist=${project.videoId}&controls=0`"
              allow="autoplay"
            ></iframe>
          </div>

          <!-- Bottom divider -->
          <div class="mt-6 flex items-center gap-3">
            <div class="h-px flex-1 bg-zinc-800 group-hover:bg-pink-500 transition-colors duration-300"></div>
            <div class="flex items-center gap-3">
              <span 
                class="font-mono text-xs text-zinc-700 group-hover:text-pink-500 transition-colors duration-300"
              >
                {{ project.isDone ? '● DONE' : '○ WIP' }}
              </span>
              <a 
                v-if="project.downloadLink"
                :href="project.downloadLink"
                target="_blank"
                rel="noopener noreferrer"
                download
                @click.stop
                class="font-mono text-xs text-zinc-700 group-hover:text-pink-500 transition-colors duration-300"
              >
                ↓ DOWNLOAD
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import data from '../data/portfolioData'

const expandedId = ref(null)
</script>
