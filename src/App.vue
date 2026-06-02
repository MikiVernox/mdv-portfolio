<template>
  <div class="bg-black min-h-screen text-white selection:bg-pink-500 selection:text-black">
    <BootSequence v-if="!isBooted" @done="handleBootDone" />

    <div v-if="isBooted" class="relative">
      <Transition name="slide-up">
        <div v-if="isReady">
          <NavBar />
          <main>
            <HeroSection />
            <AboutSection />
            <ProjectsSection />
            <ExperienceSection />
            <CertificationsSection />
            <ContactSection />
          </main>
          <FooterBar />
        </div>
      </Transition>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import BootSequence from './components/BootSequence.vue'
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import CertificationsSection from './components/CertificationsSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterBar from './components/FooterBar.vue'

const isBooted = ref(false)
const isReady = ref(false)

const handleBootDone = () => {
  isBooted.value = true
  setTimeout(() => {
    isReady.value = true
  }, 100)
}
</script>
