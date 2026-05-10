<script setup lang="ts">
import { onMounted, ref } from 'vue'
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'
import { Github, ExternalLink } from 'lucide-vue-next'

gsap.registerPlugin(ScrollTrigger)

const projectsSection = ref(null)
const projectCards = ref([])

const projects = [
  {
    title: 'Smart Hearing Aid App',
    description: 'A smart hearing aid application designed to enhance accessibility for people with hearing loss, featuring an intuitive interface and optimized user experience.',
    stack: ['Vue.js', 'Python', 'TailwindCSS'],
    image: '/smart_hearing_aid_app.png',
    github: '#',
    live: '#'
  },
  {
    title: 'Cinema Reservation System',
    description: 'A cinema reservation website providing a seamless booking system with an elegant UI, allowing users to browse movies, check schedules, and reserve tickets easily.',
    stack: ['Laravel', 'Vue.js', 'MySQL'],
    image: 'https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?q=80&w=800&auto=format&fit=crop',
    github: '#',
    live: '#'
  }
]

onMounted(() => {
  projectCards.value.forEach((card, i) => {
    gsap.fromTo(card,
      { y: 100, opacity: 0 },
      {
        y: 0,
        opacity: 1,
        duration: 1,
        ease: 'power3.out',
        scrollTrigger: {
          trigger: card,
          start: 'top 85%',
        }
      }
    )
  })
})
</script>

<template>
  <section ref="projectsSection" class="relative py-32 px-6 md:px-20 bg-brand-black">
    <div class="max-w-7xl mx-auto">
      <h2 class="text-4xl md:text-6xl font-bold mb-20 tracking-tighter uppercase glow-text">Selected Works</h2>
      
      <div class="space-y-32">
        <div 
          v-for="(project, index) in projects" 
          :key="project.title"
          ref="projectCards"
          class="relative flex flex-col md:flex-row items-center gap-10 group"
          :class="{'md:flex-row-reverse': index % 2 !== 0}"
        >
          <!-- Image Container with Parallax Effect on Hover -->
          <div class="w-full md:w-3/5 relative overflow-hidden rounded-2xl aspect-video glass">
            <div class="absolute inset-0 bg-brand-purple/20 mix-blend-overlay group-hover:opacity-0 transition-opacity duration-700 z-10"></div>
            <img 
              :src="project.image" 
              :alt="project.title"
              class="w-full h-full object-cover transform scale-105 group-hover:scale-100 transition-transform duration-1000 ease-out filter grayscale group-hover:grayscale-0"
            />
          </div>

          <!-- Project Info -->
          <div class="w-full md:w-2/5 flex flex-col space-y-6 z-20">
            <h3 class="text-3xl md:text-4xl font-bold tracking-tight text-white group-hover:text-brand-purple transition-colors duration-300">{{ project.title }}</h3>
            
            <div class="glass p-6 rounded-xl -ml-0 md:-ml-12 md:mr-0 group-[.md\:flex-row-reverse]:ml-0 group-[.md\:flex-row-reverse]:mr-[-3rem] relative shadow-2xl backdrop-blur-xl">
              <p class="text-gray-300 leading-relaxed text-lg">{{ project.description }}</p>
            </div>

            <ul class="flex flex-wrap gap-4 text-brand-blue font-mono text-sm">
              <li v-for="tech in project.stack" :key="tech">{{ tech }}</li>
            </ul>

            <div class="flex items-center gap-6 pt-4">
              <a :href="'https://github.com/houssamtermoussi'" target="_blank" class="flex items-center gap-2 text-gray-400 hover:text-white transition-colors duration-300">
                <Github class="w-6 h-6" />
                <span class="font-medium">Code</span>
              </a>
              <a :href="'https://github.com/houssamtermoussi'" target="_blank" class="flex items-center gap-2 text-gray-400 hover:text-white transition-colors duration-300">
                <ExternalLink class="w-6 h-6" />
                <span class="font-medium">Live Demo</span>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
