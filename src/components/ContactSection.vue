<template>
  <section id="contact" class="py-24 bg-zinc-950 border-t border-zinc-800">
    <!-- Section Label -->
    <div class="max-w-7xl mx-auto px-6">
      <div class="flex items-center gap-4 mb-16">
        <span class="font-mono text-xs text-pink-500 uppercase tracking-widest">05 — CONTACT</span>
        <div class="h-px flex-1 bg-zinc-800"></div>
      </div>
    </div>

    <div class="max-w-7xl mx-auto px-6 grid grid-cols-1 lg:grid-cols-2 gap-16 items-start">
      <!-- Left: Statement & Links -->
      <div>
        <h2 class="font-mono text-4xl font-black text-white leading-tight">
          LET'S BUILD<br>
          SOMETHING<br>
          <span class="text-pink-500">REAL.</span>
        </h2>

        <p class="font-mono text-zinc-500 text-sm mt-6 max-w-sm leading-relaxed">
          Do you have an exciting project in mind, need assistance, or just want to say hello? Feel free to reach out! I'm always open to discussing new opportunities and collaborations.
        </p>

        <div class="mt-10 space-y-3">
          <a :href="`mailto:${data.profile.email}`" class="flex items-center gap-4 group">
            <span class="font-mono text-xs text-zinc-600 uppercase tracking-widest w-20">EMAIL</span>
            <div class="h-px w-8 bg-zinc-800 group-hover:bg-pink-500 transition-colors duration-300"></div>
            <span class="font-mono text-sm text-zinc-300 group-hover:text-pink-400 transition-colors duration-300">
              {{ data.profile.email }}
            </span>
          </a>
          <a :href="data.profile.website" target="_blank" class="flex items-center gap-4 group">
            <span class="font-mono text-xs text-zinc-600 uppercase tracking-widest w-20">WEB</span>
            <div class="h-px w-8 bg-zinc-800 group-hover:bg-pink-500 transition-colors duration-300"></div>
            <span class="font-mono text-sm text-zinc-300 group-hover:text-pink-400 transition-colors duration-300">
              {{ data.profile.website }}
            </span>
          </a>
          <a :href="`tel:${data.profile.phone}`" class="flex items-center gap-4 group">
            <span class="font-mono text-xs text-zinc-600 uppercase tracking-widest w-20">PHONE</span>
            <div class="h-px w-8 bg-zinc-800 group-hover:bg-pink-500 transition-colors duration-300"></div>
            <span class="font-mono text-sm text-zinc-300 group-hover:text-pink-400 transition-colors duration-300">
              {{ data.profile.phone }}
            </span>
          </a>
          <a :href="data.profile.social.github" target="_blank" class="flex items-center gap-4 group">
            <span class="font-mono text-xs text-zinc-600 uppercase tracking-widest w-20">GITHUB</span>
            <div class="h-px w-8 bg-zinc-800 group-hover:bg-pink-500 transition-colors duration-300"></div>
            <span class="font-mono text-sm text-zinc-300 group-hover:text-pink-400 transition-colors duration-300">
              github.com/MikiVernox
            </span>
          </a>
        </div>
      </div>

      <!-- Right: Contact Form -->
      <div class="border border-zinc-800 bg-zinc-950 p-8">
        <div class="space-y-6">
          <div class="flex flex-col">
            <input 
              v-model="formData.name"
              type="text" 
              placeholder="NAME" 
              class="w-full bg-transparent border-b border-zinc-800 font-mono text-sm text-white py-3 placeholder-zinc-700 focus:outline-none focus:border-pink-500 transition-colors duration-200"
            />
          </div>
          <div class="flex flex-col">
            <input 
              v-model="formData.email"
              type="email" 
              placeholder="EMAIL" 
              class="w-full bg-transparent border-b border-zinc-800 font-mono text-sm text-white py-3 placeholder-zinc-700 focus:outline-none focus:border-pink-500 transition-colors duration-200"
            />
          </div>
          <div class="flex flex-col">
            <textarea 
              v-model="formData.message"
              placeholder="MESSAGE" 
              rows="4" 
              class="w-full bg-transparent border-b border-zinc-800 font-mono text-sm text-white py-3 placeholder-zinc-700 focus:outline-none focus:border-pink-500 transition-colors duration-200 resize-none"
            ></textarea>
          </div>
          
          <button 
            @click="sendMail"
            class="w-full mt-8 border border-pink-500 text-pink-500 font-mono text-xs uppercase tracking-widest py-4 hover:bg-pink-500 hover:text-black transition-all duration-200"
          >
            SEND MESSAGE
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive } from 'vue'
import data from '../data/portfolioData'

const formData = reactive({
  name: '',
  email: '',
  message: ''
})

const sendMail = () => {
  if (!formData.name || !formData.email || !formData.message) {
    alert('Please fill in all fields.')
    return
  }

  const subject = encodeURIComponent(`Portfolio Contact from ${formData.name}`)
  const body = encodeURIComponent(
    `Name: ${formData.name}\n` +
    `Email: ${formData.email}\n\n` +
    `Message:\n${formData.message}`
  )
  
  window.location.href = `mailto:${data.profile.email}?subject=${subject}&body=${body}`
}
</script>
