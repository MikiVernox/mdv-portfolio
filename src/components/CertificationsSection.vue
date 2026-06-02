<template>
  <section id="certifications" class="py-24 bg-black border-t border-zinc-800">
    <!-- Section Label -->
    <div class="max-w-7xl mx-auto px-6">
      <div class="flex items-center gap-4 mb-16">
        <span class="font-mono text-xs text-pink-500 uppercase tracking-widest">04 — CERTIFICATIONS</span>
        <div class="h-px flex-1 bg-zinc-800"></div>
      </div>
    </div>

    <div class="max-w-7xl mx-auto px-6">
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-px bg-zinc-800">
        <div 
          v-for="cert in data.certifications" 
          :key="cert.id"
          class="bg-zinc-950 p-6 hover:bg-zinc-900 transition-colors duration-300 group cursor-pointer"
          @click="selectedCert = cert"
        >
          <!-- Certificate image -->
          <div class="border border-zinc-800 group-hover:border-pink-500 transition-colors duration-300 mb-4 overflow-hidden aspect-[4/3]">
            <img :src="cert.image" :alt="cert.name"
              class="w-full h-full object-cover opacity-70 group-hover:opacity-100 transition-opacity duration-300" />
          </div>

          <!-- Name -->
          <h3 class="font-mono text-white text-sm font-bold leading-tight">{{ cert.name }}</h3>

          <!-- Issuer + Year -->
          <p class="font-mono text-xs text-purple-400 mt-2">{{ cert.issuer }}</p>
          <p class="font-mono text-xs text-zinc-600 mt-1">{{ cert.year }}</p>
        </div>
      </div>
    </div>

    <!-- Lightbox Modal -->
    <Transition name="fade">
      <div 
        v-if="selectedCert" 
        class="fixed inset-0 z-[100] bg-black/95 flex items-center justify-center p-4 cursor-zoom-out"
        @click="selectedCert = null"
      >
        <!-- Close Button -->
        <button class="absolute top-8 right-8 font-mono text-white text-xl hover:text-pink-500 transition-colors">
          ✕ CLOSE
        </button>

        <div class="relative max-w-5xl w-full flex flex-col items-center">
          <img 
            :src="selectedCert.image" 
            :alt="selectedCert.name"
            class="max-w-full max-h-[85vh] object-contain border border-zinc-800 shadow-2xl"
            @click.stop
          />
          <div class="mt-6 text-center">
            <h3 class="font-mono text-white text-lg font-bold">{{ selectedCert.name }}</h3>
            <p class="font-mono text-zinc-400 text-sm">{{ selectedCert.issuer }} • {{ selectedCert.year }}</p>
          </div>
        </div>
      </div>
    </Transition>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import data from '../data/portfolioData'

const selectedCert = ref(null)
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
