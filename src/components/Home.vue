<script setup lang="ts">
import { ArrowRight, Download, MapPin, Calendar, Award } from 'lucide-vue-next'
</script>

<template>
  <div class="min-h-screen flex items-center justify-center px-8 md:px-16 lg:px-24 pt-20">
    <div class="max-w-7xl w-full grid md:grid-cols-2 gap-16 lg:gap-24 items-center">
      <!-- Left side - Info -->
      <div class="space-y-8 order-2 md:order-1 py-8">
        <!-- Badge -->
        <div class="inline-flex items-center gap-3 border border-blue-500/30 bg-blue-500/10 backdrop-blur px-4 py-2">
          <div class="w-2 h-2 bg-green-400 rounded-full animate-pulse"></div>
          <span class="text-sm text-blue-400 tracking-wider">Disponible pour nouveaux projets</span>
        </div>

        <!-- Title with animated underline -->
        <div class="space-y-6">
          <div class="relative inline-block">
            <div class="text-xs text-blue-400 tracking-[0.3em] uppercase mb-2">Hello, je suis</div>
            <h1 class="text-6xl lg:text-7xl tracking-tight">
              <span class="bg-gradient-to-r from-white via-blue-100 to-white bg-clip-text text-transparent">
                Johary
              </span>
            </h1>
            <h2 class="text-5xl lg:text-6xl tracking-tight">
              <span class="bg-gradient-to-r from-blue-400 via-violet-400 to-blue-400 bg-clip-text text-transparent">
                Fiononana
              </span>
            </h2>
            
            <!-- Animated decorative lines -->
            <div class="absolute -left-4 top-0 w-1 h-full bg-gradient-to-b from-blue-500 via-violet-500 to-transparent"></div>
            <div class="mt-4 flex items-center gap-2">
              <div class="w-16 h-px bg-gradient-to-r from-blue-500 to-transparent"></div>
              <div class="w-2 h-2 bg-blue-500 rotate-45"></div>
              <div class="w-24 h-px bg-gradient-to-r from-blue-500 via-violet-500 to-transparent"></div>
            </div>
          </div>

          <!-- Subtitle with geometric elements -->
          <div class="relative pl-6 border-l-2 border-blue-500/30">
            <h3 class="text-2xl lg:text-3xl text-slate-200 tracking-wide">
              Développeur Full Stack
            </h3>
            <div class="absolute -left-1 top-0 w-2 h-2 bg-blue-500 rotate-45"></div>
            <div class="absolute -left-1 bottom-0 w-2 h-2 bg-violet-500 rotate-45"></div>
          </div>
        </div>

        <!-- Description -->
        <p class="text-slate-200/75 max-w-xl leading-relaxed text-lg relative">
          <span class="text-3xl text-blue-500/30 absolute -left-4 -top-2">"</span>
          Spécialisé dans la création de solutions robustes et sur mesure, avec
          un code de qualité et une attention rigoureuse à la fidélité du design.
          Prêt à concevoir des applications parfaitement alignées avec les
          exigences de chaque projet.
          <span class="text-3xl text-blue-500/30 absolute -right-2 bottom-0">"</span>
        </p>

        <!-- Info cards -->
        <div class="grid grid-cols-3 gap-4">
          <div class="border border-slate-800 bg-slate-900/50 backdrop-blur p-4 hover:border-blue-500/50 transition-all group">
            <MapPin class="w-5 h-5 text-blue-400 mb-2 group-hover:scale-110 transition-transform" />
            <div class="text-xs text-slate-400 uppercase tracking-wider mb-1">Localisation</div>
            <div class="text-sm text-white">Madagascar</div>
          </div>
          <div class="border border-slate-800 bg-slate-900/50 backdrop-blur p-4 hover:border-violet-500/50 transition-all group">
            <Calendar class="w-5 h-5 text-violet-400 mb-2 group-hover:scale-110 transition-transform" />
            <div class="text-xs text-slate-400 uppercase tracking-wider mb-1">Expérience</div>
            <div class="text-sm text-white">5+ ans</div>
          </div>
          <div class="border border-slate-800 bg-slate-900/50 backdrop-blur p-4 hover:border-cyan-500/50 transition-all group">
            <Award class="w-5 h-5 text-cyan-400 mb-2 group-hover:scale-110 transition-transform" />
            <div class="text-xs text-slate-400 uppercase tracking-wider mb-1">Projets</div>
            <div class="text-sm text-white">50+ réalisés</div>
          </div>
        </div>

        <!-- CTA Buttons -->
        <div class="flex flex-wrap gap-4 pt-4">
          <button class="group relative px-8 py-4 border-2 border-blue-500 bg-blue-500 text-white overflow-hidden hover:border-blue-400 transition-all">
            <span class="relative z-10 flex items-center gap-2">
              Contactez-moi
              <ArrowRight class="w-4 h-4 group-hover:translate-x-1 transition-transform" />
            </span>
            <div class="absolute inset-0 bg-gradient-to-r from-blue-600 to-violet-600 opacity-0 group-hover:opacity-100 transition-opacity"></div>
          </button>
          <button class="group relative px-8 py-4 border-2 border-slate-700 bg-transparent text-white overflow-hidden hover:border-blue-500 transition-all">
            <span class="relative z-10 flex items-center gap-2">
              Télécharger CV
              <Download class="w-4 h-4 group-hover:translate-y-1 transition-transform" />
            </span>
            <div class="absolute inset-0 bg-blue-500/10 opacity-0 group-hover:opacity-100 transition-opacity"></div>
          </button>
        </div>

        <!-- Tech stack showcase -->
        <div class="pt-8 border-t border-slate-800">
          <div class="text-xs text-slate-300 uppercase tracking-widest mb-4">Technologies maîtrisées</div>
          <div class="flex flex-wrap gap-3">
            <div 
              v-for="(tech, index) in ['React', 'Next.js', 'Laravel', 'Symfony', 'AWS', 'Python']"
              :key="index"
              class="group relative px-4 py-2 border border-slate-500 bg-slate-900/30 hover:border-blue-200/80 transition-all cursor-pointer"
            >
              <span class="text-sm text-slate-400 group-hover:text-blue-400 transition-colors">{{ tech }}</span>
              <div class="absolute bottom-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-blue-500 to-transparent scale-x-0 group-hover:scale-x-100 transition-transform"></div>
            </div>
          </div>
        </div>
      </div>

      <!-- Right side - Image with complex decorations -->
      <div class="flex justify-center md:justify-start order-1 md:order-2">
        <div class="relative">
          <!-- Main image container with geometric frame -->
          <div class="relative w-96 h-[500px]">
            <!-- Geometric frame elements -->
            <div class="absolute -top-8 -left-8 w-24 h-24 border-t-2 border-l-2 border-blue-500/50"></div>
            <div class="absolute -bottom-8 -right-8 w-24 h-24 border-b-2 border-r-2 border-violet-500/50"></div>

            <!-- Main border -->
            <div class="relative w-full h-full border-2 border-slate-800 bg-slate-900/50 backdrop-blur overflow-hidden group">
              <!-- Placeholder for image -->
              <div class="w-full h-full bg-gradient-to-br from-blue-600/20 via-violet-600/20 to-cyan-600/20 flex items-center justify-center">
                <div class="text-6xl text-slate-700">JF</div>
              </div>

              <!-- Gradient overlay -->
              <div class="absolute inset-0 bg-gradient-to-t from-slate-950 via-transparent to-transparent opacity-60"></div>

              <!-- Hover effect -->
              <div class="absolute inset-0 bg-gradient-to-br from-blue-500/20 to-violet-500/20 opacity-0 group-hover:opacity-100 transition-all duration-500"></div>

              <!-- Stats overlay -->
              <div class="absolute bottom-8 left-0 right-0 px-6 flex justify-between gap-4">
                <div class="flex-1 border border-blue-500/30 bg-slate-950/90 backdrop-blur p-3">
                  <div class="text-2xl bg-gradient-to-r from-blue-400 to-violet-400 bg-clip-text text-transparent">5+</div>
                  <div class="text-xs text-slate-500 uppercase tracking-wider">Années</div>
                </div>
                <div class="flex-1 border border-violet-500/30 bg-slate-950/90 backdrop-blur p-3">
                  <div class="text-2xl bg-gradient-to-r from-violet-400 to-blue-400 bg-clip-text text-transparent">50+</div>
                  <div class="text-xs text-slate-500 uppercase tracking-wider">Projets</div>
                </div>
                <div class="flex-1 border border-cyan-500/30 bg-slate-950/90 backdrop-blur p-3">
                  <div class="text-2xl bg-gradient-to-r from-cyan-400 to-blue-400 bg-clip-text text-transparent">30+</div>
                  <div class="text-xs text-slate-500 uppercase tracking-wider">Clients</div>
                </div>
              </div>
            </div>

            <!-- Animated circular elements -->
            <div 
              class="absolute top-1/4 -right-12 w-24 h-24 rounded-full border-2 border-blue-500/30 flex items-center justify-center animate-spin" 
              style="animation-duration: 20s"
            >
              <div class="w-16 h-16 rounded-full border-2 border-violet-500/30"></div>
            </div>
            <div 
              class="absolute bottom-1/4 -left-12 w-20 h-20 rounded-full border-2 border-violet-500/30 flex items-center justify-center animate-spin" 
              style="animation-duration: 15s; animation-direction: reverse"
            >
              <div class="w-12 h-12 rounded-full border-2 border-blue-500/30"></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
