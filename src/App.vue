<script setup lang="ts">
import { onMounted, onUnmounted } from 'vue'
import Lenis from 'lenis'
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'

import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ParallaxShowcase from './components/ParallaxShowcase.vue'
import FooterSection from './components/FooterSection.vue'

gsap.registerPlugin(ScrollTrigger)

let lenis: Lenis

onMounted(() => {
  // Initialize Lenis
  lenis = new Lenis({
    duration: 1.2,
    easing: (t) => Math.min(1, 1.001 - Math.pow(2, -10 * t)),
    orientation: 'vertical',
    gestureOrientation: 'vertical',
    smoothWheel: true,
    wheelMultiplier: 1,
    touchMultiplier: 2,
    infinite: false,
  })

  // Synchronize Lenis with GSAP ScrollTrigger
  lenis.on('scroll', ScrollTrigger.update)

  gsap.ticker.add((time) => {
    lenis.raf(time * 1000)
  })

  gsap.ticker.lagSmoothing(0)
})

onUnmounted(() => {
  if (lenis) {
    lenis.destroy()
  }
})
</script>

<template>
  <main class="bg-brand-black text-white min-h-screen selection:bg-brand-purple/30 selection:text-white">
    <HeroSection />
    <AboutSection />
    <SkillsSection />
    <ParallaxShowcase />
    <ProjectsSection />
    <FooterSection />
  </main>
</template>

<style>
/* Any App-specific overrides can go here */
</style>
