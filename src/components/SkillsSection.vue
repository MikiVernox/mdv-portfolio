<template>
  <section id="skills" class="py-24 bg-black border-t border-zinc-800">
    <!-- Section Label -->
    <div class="max-w-7xl mx-auto px-6">
      <div class="flex items-center gap-4 mb-16">
        <span class="font-mono text-xs text-pink-500 uppercase tracking-widest">01 — SKILLS</span>
        <div class="h-px flex-1 bg-zinc-800"></div>
      </div>
    </div>

    <div class="max-w-7xl mx-auto px-6 grid grid-cols-1 md:grid-cols-2 gap-12">
      <!-- Left Column: Skill Bars -->
      <div>
        <div 
          v-for="skill in skills" 
          :key="skill.name" 
          class="mb-6"
        >
          <div class="flex justify-between items-center mb-2">
            <span class="font-mono text-xs text-zinc-300 uppercase tracking-widest">{{ skill.name }}</span>
            <span class="font-mono text-xs text-pink-500">{{ skill.level }}%</span>
          </div>
          <div class="h-px bg-zinc-800 relative">
            <div
              class="h-px bg-gradient-to-r from-pink-500 to-purple-500 transition-all duration-1000 ease-out"
              :style="{ width: animated ? skill.level + '%' : '0%' }"
            ></div>
          </div>
          <div class="font-mono text-xs text-zinc-600 mt-1">{{ skill.tag }}</div>
        </div>
      </div>

      <!-- Right Column: Tags Block -->
      <div class="flex flex-wrap content-start items-start">
        <div class="w-full border border-zinc-800 bg-zinc-900 p-6">
          <div class="flex flex-wrap">
            <span 
              v-for="tag in allTags" 
              :key="tag" 
              class="inline-block border border-zinc-700 font-mono text-xs text-zinc-400 px-3 py-1 m-1 hover:border-pink-500 hover:text-pink-400 transition-all duration-200"
            >
              {{ tag }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const skills = [
  { name: 'GDScript',        level: 92, tag: 'Godot 4 — primary scripting' },
  { name: 'C++',             level: 78, tag: 'Unreal Engine / systems' },
  { name: 'Godot 4',         level: 90, tag: 'Engine — primary' },
  { name: 'Unreal Engine 5', level: 75, tag: 'Engine — secondary / Blueprints' },
  { name: 'Game Architecture', level: 88, tag: 'State machines, ECS patterns' },
  { name: 'AI Agent Systems', level: 85, tag: 'Navigation, movement, behavior trees' },
  { name: 'Python',          level: 70, tag: 'Tooling, automation, local AI' },
  { name: 'Shader / VFX',   level: 60, tag: 'GLSL, Godot shaders' },
]

const allTags = [
  'GODOT 4', 'UNREAL ENGINE 5', 'C++', 'GDSCRIPT', 'BLUEPRINTS',
  'STATE MACHINES', 'PHYSICS', 'AI MOVEMENT', 'SQLITE', 'PYTHON',
  'LOCAL AI', 'OLLAMA', 'GAME SYSTEMS', 'EDITOR PLUGINS'
]

const animated = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        animated.value = true
        observer.disconnect()
      }
    })
  }, { threshold: 0.1 })

  observer.observe(document.querySelector('#skills'))
})
</script>
