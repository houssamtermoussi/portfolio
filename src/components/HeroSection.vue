<script setup lang="ts">
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const hero = ref(null)
const title = ref(null)
const subtitle = ref(null)
const bgParallax = ref(null)

onMounted(() => {
  const tl = gsap.timeline()
  
  tl.fromTo(title.value, 
    { y: 100, opacity: 0 }, 
    { y: 0, opacity: 1, duration: 1.5, ease: 'power4.out', delay: 0.2 }
  )
  .fromTo(subtitle.value,
    { y: 50, opacity: 0 },
    { y: 0, opacity: 1, duration: 1, ease: 'power3.out' },
    "-=1"
  )

  // Mouse Parallax effect
  const handleMouseMove = (e: MouseEvent) => {
    const { clientX, clientY } = e
    const x = (clientX / window.innerWidth - 0.5) * 40
    const y = (clientY / window.innerHeight - 0.5) * 40
    
    gsap.to(bgParallax.value, {
      x,
      y,
      duration: 1,
      ease: 'power2.out'
    })
  }
  
  window.addEventListener('mousemove', handleMouseMove)
})
</script>

<template>
  <section ref="hero" class="relative h-screen w-full flex items-center justify-center overflow-hidden bg-brand-black">
    <!-- Animated background layer -->
    <div ref="bgParallax" class="absolute inset-0 z-0 opacity-40">
      <div class="absolute top-1/4 left-1/4 w-[40vw] h-[40vw] bg-brand-purple rounded-full mix-blend-screen filter blur-[120px] animate-float"></div>
      <div class="absolute bottom-1/4 right-1/4 w-[35vw] h-[35vw] bg-brand-blue rounded-full mix-blend-screen filter blur-[100px] animate-float" style="animation-delay: -3s;"></div>
    </div>

    <!-- Content -->
    <div class="relative z-10 text-center px-4">
      <h1 ref="title" class="text-6xl md:text-8xl font-bold tracking-tighter mb-4 glow-text uppercase">
        Houssam Termoussi
      </h1>
      <div ref="subtitle" class="space-y-4">
        <h2 class="text-2xl md:text-3xl text-gray-300 font-light">Full-Stack Developer</h2>
        <p class="text-xl md:text-2xl text-gray-400 italic font-serif">"Creating immersive web & mobile experiences."</p>
      </div>
    </div>

    <!-- Scroll Indicator -->
    <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 z-10 flex flex-col items-center">
      <span class="text-xs uppercase tracking-widest text-gray-500 mb-2">Scroll</span>
      <div class="w-[1px] h-16 bg-gradient-to-b from-gray-500 to-transparent"></div>
    </div>
  </section>
</template>
