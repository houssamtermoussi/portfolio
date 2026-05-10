<script setup lang="ts">
import { onMounted, ref } from 'vue'
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const showcaseSection = ref(null)
const stickyContainer = ref(null)
const textLayer1 = ref(null)
const textLayer2 = ref(null)
const boxLayer = ref(null)

onMounted(() => {
  const tl = gsap.timeline({
    scrollTrigger: {
      trigger: showcaseSection.value,
      start: 'top top',
      end: '+=200%',
      scrub: 1,
      pin: true,
      anticipatePin: 1
    }
  })

  // Deep parallax effects
  tl.to(boxLayer.value, { scale: 5, opacity: 0, duration: 1 })
    .fromTo(textLayer1.value, { y: 100, opacity: 0 }, { y: -50, opacity: 1, duration: 1 }, 0)
    .to(textLayer1.value, { y: -200, opacity: 0, duration: 1 }, 1)
    .fromTo(textLayer2.value, { scale: 0.5, opacity: 0 }, { scale: 1, opacity: 1, duration: 1 }, 1)
    .to(textLayer2.value, { scale: 1.5, opacity: 0, duration: 1 }, 2)
})
</script>

<template>
  <section ref="showcaseSection" class="relative h-screen w-full bg-brand-black overflow-hidden flex items-center justify-center">
    <!-- Pinned Container -->
    <div ref="stickyContainer" class="relative w-full h-full flex items-center justify-center">
      
      <!-- Depth Box -->
      <div ref="boxLayer" class="absolute w-[30vw] h-[30vw] border-[1px] border-brand-purple/30 rounded-full flex items-center justify-center">
        <div class="w-[20vw] h-[20vw] border-[1px] border-brand-blue/30 rounded-full"></div>
      </div>

      <!-- Text Layers -->
      <div ref="textLayer1" class="absolute text-center">
        <h2 class="text-5xl md:text-7xl font-bold tracking-widest text-transparent bg-clip-text bg-gradient-to-b from-white to-gray-500 uppercase">
          Infinite Depth
        </h2>
      </div>

      <div ref="textLayer2" class="absolute text-center opacity-0">
        <h2 class="text-5xl md:text-8xl font-bold tracking-tighter glow-text text-white uppercase">
          Immersive
        </h2>
        <p class="text-2xl text-brand-blue mt-4 font-light tracking-widest">Experiences</p>
      </div>

    </div>
  </section>
</template>
