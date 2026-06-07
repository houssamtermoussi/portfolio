<script setup lang="ts">
import { Github, Linkedin, Mail } from 'lucide-vue-next'
</script>

<template>
  <footer class="py-16 border-t border-white/10 bg-brand-black relative z-10">
    <div class="max-w-7xl mx-auto px-6 md:px-20 grid grid-cols-1 md:grid-cols-3 gap-6 items-center">
      
      <!-- Left -->
      <p class="text-gray-500 text-sm tracking-widest uppercase text-center md:text-left">
        © 2026 Houssam Termoussi
      </p>

      <!-- Center (Social Links) -->
      <div class="flex items-center justify-center gap-6">
        <a href="https://github.com/houssamtermoussi" target="_blank" class="text-gray-500 hover:text-white hover:scale-110 hover:shadow-[0_0_15px_rgba(139,92,246,0.5)] rounded-full transition-all duration-300">
          <Github class="w-5 h-5" />
        </a>
        <a href="https://www.linkedin.com/in/houssam-termoussi-6b10163bb/" target="_blank" class="text-gray-500 hover:text-white hover:scale-110 hover:shadow-[0_0_15px_rgba(59,130,246,0.5)] rounded-full transition-all duration-300">
          <Linkedin class="w-5 h-5" />
        </a>
        <a href="mailto:houssam111888@gmail.com" class="text-gray-500 hover:text-white hover:scale-110 hover:shadow-[0_0_15px_rgba(255,255,255,0.5)] rounded-full transition-all duration-300">
          <Mail class="w-5 h-5" />
        </a>
      </div>

      <!-- Right -->
      <div class="flex items-center justify-center md:justify-end gap-2 text-gray-500 text-sm">
        <span>Built with</span>
        <span class="text-brand-purple font-medium">Vue</span>
        <span>&</span>
        <span class="text-brand-blue font-medium">GSAP</span>
      </div>
      
    </div>
  </footer>
</template>
