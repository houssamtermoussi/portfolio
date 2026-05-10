<script setup lang="ts">
import { onMounted, ref } from 'vue'
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'
import { Send, Linkedin, Github, Mail } from 'lucide-vue-next'

gsap.registerPlugin(ScrollTrigger)

const contactSection = ref(null)
const formRef = ref(null)

onMounted(() => {
  gsap.fromTo(formRef.value,
    { y: 50, opacity: 0 },
    {
      y: 0,
      opacity: 1,
      duration: 1,
      ease: 'power3.out',
      scrollTrigger: {
        trigger: contactSection.value,
        start: 'top 70%',
      }
    }
  )
})
</script>

<template>
  <section ref="contactSection" class="relative py-32 px-6 md:px-20 bg-brand-black">
    <!-- Ambient Glow -->
    <div class="absolute bottom-0 right-0 w-[40vw] h-[40vw] bg-brand-blue/10 rounded-full blur-[120px] pointer-events-none"></div>

    <div class="max-w-4xl mx-auto">
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-6xl font-bold tracking-tighter uppercase glow-text mb-4">Let's Talk</h2>
        <p class="text-xl text-gray-400 font-light">Prêt à créer votre prochaine expérience web ?</p>
      </div>

      <div ref="formRef" class="glass rounded-3xl p-8 md:p-12 relative z-10">
        <form class="space-y-6" @submit.prevent>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <div class="space-y-2">
              <label class="text-sm font-medium text-gray-400 ml-2">Name</label>
              <input type="text" class="w-full bg-white/5 border border-white/10 rounded-xl px-4 py-4 text-white focus:outline-none focus:border-brand-purple/50 focus:ring-1 focus:ring-brand-purple/50 transition-all" placeholder="John Doe" />
            </div>
            <div class="space-y-2">
              <label class="text-sm font-medium text-gray-400 ml-2">Email</label>
              <input type="email" class="w-full bg-white/5 border border-white/10 rounded-xl px-4 py-4 text-white focus:outline-none focus:border-brand-blue/50 focus:ring-1 focus:ring-brand-blue/50 transition-all" placeholder="john@example.com" />
            </div>
          </div>
          <div class="space-y-2">
            <label class="text-sm font-medium text-gray-400 ml-2">Message</label>
            <textarea rows="4" class="w-full bg-white/5 border border-white/10 rounded-xl px-4 py-4 text-white focus:outline-none focus:border-brand-purple/50 focus:ring-1 focus:ring-brand-purple/50 transition-all resize-none" placeholder="Hello..."></textarea>
          </div>
          
          <button class="w-full relative group overflow-hidden rounded-xl bg-white/5 border border-white/10 p-4 transition-all hover:border-brand-purple/50">
            <div class="absolute inset-0 bg-gradient-to-r from-brand-purple/20 to-brand-blue/20 translate-y-[100%] group-hover:translate-y-[0%] transition-transform duration-300"></div>
            <span class="relative z-10 flex items-center justify-center gap-2 text-white font-medium tracking-wide">
              Send Message <Send class="w-4 h-4" />
            </span>
          </button>
        </form>

        <!-- Social Links -->
        <div class="mt-12 pt-8 border-t border-white/10 flex justify-center gap-8">
          <a href="#" class="p-3 rounded-full bg-white/5 text-gray-400 hover:text-white hover:bg-brand-purple/20 hover:scale-110 transition-all duration-300 group">
            <Github class="w-6 h-6 group-hover:glow-box rounded-full" />
          </a>
          <a href="#" class="p-3 rounded-full bg-white/5 text-gray-400 hover:text-white hover:bg-brand-blue/20 hover:scale-110 transition-all duration-300 group">
            <Linkedin class="w-6 h-6 group-hover:glow-box rounded-full" />
          </a>
          <a href="#" class="p-3 rounded-full bg-white/5 text-gray-400 hover:text-white hover:bg-white/20 hover:scale-110 transition-all duration-300 group">
            <Mail class="w-6 h-6 group-hover:glow-box rounded-full" />
          </a>
        </div>
      </div>
    </div>
  </section>
</template>
