<script setup lang="ts">
import { onMounted, ref } from 'vue'
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'
import { Braces, Atom, Smartphone, Server, Code2, Globe, Database, HardDrive, FolderTree } from 'lucide-vue-next'

gsap.registerPlugin(ScrollTrigger)

const skillsSection = ref(null)
const skillsCards = ref([])

const skills = [
  // Ligne 1 — Frontend
  { name: 'React.js', icon: Atom, color: 'text-blue-400', glow: 'shadow-blue-400/50' },
  { name: 'Vue.js', icon: Braces, color: 'text-green-500', glow: 'shadow-green-500/50' },
  { name: 'Flutter', icon: Smartphone, color: 'text-cyan-400', glow: 'shadow-cyan-400/50' },
  // Ligne 2 — Backend
  { name: 'Laravel', icon: Server, color: 'text-red-500', glow: 'shadow-red-500/50' },
  { name: 'Express.js', icon: Code2, color: 'text-gray-300', glow: 'shadow-gray-300/50' },
  { name: 'Next.js', icon: Globe, color: 'text-white', glow: 'shadow-white/50' },
  // Ligne 3 — Database
  { name: 'MySQL', icon: Database, color: 'text-blue-300', glow: 'shadow-blue-300/50' },
  { name: 'PostgreSQL', icon: HardDrive, color: 'text-indigo-400', glow: 'shadow-indigo-400/50' },
  { name: 'MongoDB', icon: FolderTree, color: 'text-green-400', glow: 'shadow-green-400/50' },
]

onMounted(() => {
  gsap.fromTo(skillsCards.value, 
    { y: 50, opacity: 0, scale: 0.8 },
    {
      y: 0,
      opacity: 1,
      scale: 1,
      duration: 0.8,
      stagger: 0.1,
      ease: 'back.out(1.7)',
      scrollTrigger: {
        trigger: skillsSection.value,
        start: 'top 75%',
      }
    }
  )
})
</script>

<template>
  <section ref="skillsSection" class="relative py-32 px-6 md:px-20 bg-brand-black">
    <div class="max-w-6xl mx-auto">
      <h2 class="text-4xl md:text-6xl font-bold mb-16 text-center tracking-tighter uppercase glow-text">Core Stack</h2>
      
      <div class="grid grid-cols-2 md:grid-cols-3 gap-8">
        <div 
          v-for="(skill, index) in skills" 
          :key="skill.name"
          ref="skillsCards"
          class="glass group relative p-8 rounded-2xl flex flex-col items-center justify-center transition-all duration-500 hover:-translate-y-2 hover:bg-white/10"
        >
          <!-- Animated Background Glow on Hover -->
          <div class="absolute inset-0 rounded-2xl opacity-0 group-hover:opacity-100 transition-opacity duration-500 blur-xl" :class="skill.glow"></div>
          
          <component 
            :is="skill.icon" 
            class="w-16 h-16 mb-6 transition-transform duration-500 group-hover:scale-110 group-hover:animate-float"
            :class="skill.color"
          />
          <h3 class="text-xl font-medium text-gray-200 group-hover:text-white transition-colors">{{ skill.name }}</h3>
        </div>
      </div>
    </div>
  </section>
</template>
