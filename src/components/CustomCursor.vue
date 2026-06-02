<template>
  <div
    class="custom-cursor-container pointer-events-none fixed inset-0 z-[9999]"
    ref="cursorContainer"
  >
    <!-- The Dot (Crosshair) -->
    <div 
      class="custom-cursor-dot absolute rounded-full bg-pink-500 pointer-events-none transition-transform duration-75 ease-out"
      :style="dotStyle"
    ></div>
    
    <!-- The Aura (Ring) -->
    <div 
      class="custom-cursor-aura absolute rounded-full border border-purple-500/50 pointer-events-none transition-transform duration-150 ease-out"
      :style="auraStyle"
    ></div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue'

const cursorContainer = ref(null)
const mouseX = ref(0)
const mouseY = ref(0)
const isClicking = ref(false)
const isHovering = ref(false)

const dotStyle = computed(() => ({
  left: `${mouseX.value}px`,
  top: `${mouseY.value}px`,
  transform: `translate(-50%, -50%) scale(${isClicking.value ? 0.8 : 1})`,
}))

const auraStyle = computed(() => ({
  left: `${mouseX.value}px`,
  top: `${mouseY.value}px`,
  width: `${isHovering.value ? 50 : 30}px`,
  height: `${isHovering.value ? 50 : 30}px`,
  transform: `translate(-50%, -50%) scale(${isClicking.value ? 1.5 : 1})`,
  opacity: isClicking.value ? 0.3 : 0.5,
}))

const handleMouseMove = (e) => {
  mouseX.value = e.clientX
  mouseY.value = e.clientY
}

const handleMouseDown = () => {
  isClicking.value = true
}

const handleMouseUp = () => {
  isClicking.value = false
}

const handleMouseOver = (e) => {
  // Check if the hovered element is interactive
  const target = e.target
  const isInteractive = 
    target.closest('a') || 
    target.closest('button') || 
    target.closest('input') || 
    target.closest('textarea') ||
    target.closest('.cursor-pointer')

  isHovering.value = !!isInteractive
}

onMounted(() => {
  window.addEventListener('mousemove', handleMouseMove)
  window.addEventListener('mousedown', handleMouseDown)
  window.addEventListener('mouseup', handleMouseUp)
  window.addEventListener('mouseover', handleMouseOver)
})

onUnmounted(() => {
  window.removeEventListener('mousemove', handleMouseMove)
  window.removeEventListener('mousedown', handleMouseDown)
  window.removeEventListener('mouseup', handleMouseUp)
  window.removeEventListener('mouseover', handleMouseOver)
})
</script>

<style scoped>
.custom-cursor-dot {
  width: 6px;
  height: 6px;
}

.custom-cursor-aura {
  transition: width 0.2s ease, height 0.2s ease, transform 0.15s ease-out, opacity 0.15s ease-out;
}
</style>
