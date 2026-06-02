<template>
  <Transition name="fade">
    <div v-if="visible" class="w-full h-screen bg-black flex flex-col items-center justify-center p-6">
      <div class="max-w-md w-full space-y-2">
        <div 
          v-for="(line, i) in lines" 
          :key="i" 
          class="font-mono text-sm text-pink-400 transition-opacity duration-300"
          :class="line ? 'opacity-100' : 'opacity-0'"
        >
          {{ bootText[i] }}
        </div>
        
        <div class="mt-8">
          <div class="h-px w-full bg-zinc-800 overflow-hidden">
            <div 
              class="h-px bg-gradient-to-r from-pink-500 to-purple-500 transition-all duration-[1800ms] ease-out"
              :style="{ width: progress + '%' }"
            ></div>
          </div>
        </div>
      </div>
    </div>
  </Transition>
</template>

<script setup>
import { onMounted, ref } from 'vue'

const emit = defineEmits(['done'])
const visible = ref(true)
const progress = ref(0)
const bootText = [
  '> INITIALIZING MDV ENGINE...',
  '> LOADING MODULES: [GAME DEV] [C++] [GODOT] [UE5]',
  '> MOUNTING PORTFOLIO...',
  '> WELCOME, OPERATOR.'
]
const lines = ref([false, false, false, false])

onMounted(() => {
  // Trigger progress bar
  setTimeout(() => {
    progress.value = 100
  }, 50)

  // Trigger text lines
  lines.value.forEach((_, i) => {
    setTimeout(() => { 
      lines.value[i] = true 
    }, i * 400)
  })

  // Finish sequence
  setTimeout(() => {
    visible.value = false
    setTimeout(() => emit('done'), 600) // wait for fade transition
  }, 2200)
})
</script>

<style scoped>
.fade-leave-active {
  transition: opacity 0.6s ease;
}
.fade-leave-to {
  opacity: 0;
}
</style>
