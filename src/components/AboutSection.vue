<script setup lang="ts">
import { onMounted, ref } from 'vue'
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const aboutSection = ref(null)
const textRef = ref(null)
const glassCard = ref(null)

onMounted(() => {
  const tl = gsap.timeline({
    scrollTrigger: {
      trigger: aboutSection.value,
      start: 'top 70%',
      end: 'bottom 20%',
      toggleActions: 'play none none reverse'
    }
  })

  tl.fromTo(glassCard.value,
    { y: 100, opacity: 0, scale: 0.9 },
    { y: 0, opacity: 1, scale: 1, duration: 1, ease: 'power3.out' }
  )
  .fromTo(textRef.value,
    { opacity: 0, y: 20 },
    { opacity: 1, y: 0, duration: 1, ease: 'power2.out' },
    "-=0.5"
  )

  // Light Parallax on scroll for the background element
  gsap.to('.about-bg-element', {
    y: 150,
    ease: 'none',
    scrollTrigger: {
      trigger: aboutSection.value,
      start: 'top bottom',
      end: 'bottom top',
      scrub: true
    }
  })
})
</script>

<template>
  <section ref="aboutSection" class="relative py-32 px-6 md:px-20 min-h-[80vh] flex items-center justify-center overflow-hidden">
    <!-- Abstract Parallax Background Element -->
    <div class="about-bg-element absolute top-0 left-0 w-[50vw] h-[50vw] rounded-full bg-brand-purple/5 blur-[150px] -z-10 pointer-events-none"></div>

    <div class="max-w-4xl w-full mx-auto">
      <div ref="glassCard" class="glass rounded-3xl p-10 md:p-16 relative z-10 overflow-hidden group hover:border-brand-purple/30 transition-colors duration-500">
        <!-- Shine effect on hover -->
        <div class="absolute inset-0 bg-gradient-to-tr from-white/0 via-white/5 to-white/0 opacity-0 group-hover:opacity-100 transition-opacity duration-700 transform -translate-x-full group-hover:translate-x-full"></div>
        
        <h2 class="text-3xl md:text-5xl font-bold mb-8 glow-text tracking-wide uppercase">About Me</h2>
        
        <p ref="textRef" class="text-xl md:text-3xl font-light leading-relaxed text-gray-200">
          Fullstack developer passionate about building <span class="text-brand-blue font-medium">modern </span>, high-performance web <span class="text-brand-purple font-medium">applications</span> with immersive user experiences, smooth interfaces, and strong, scalable<span class="text-white font-medium glow-text"> backend logic</span>.
        </p>
      </div>
    </div>
  </section>
</template>
