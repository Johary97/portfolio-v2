<script setup lang="ts">
import { ref, computed } from 'vue'
import { useI18n } from 'vue-i18n'
import Navigation from '@components/Navigation.vue'
import Home from '@components/Home.vue'
import Services from '@components/Services.vue'
import Skills from '@components/Skills.vue'
import Journey from '@components/Journey.vue'
import Contact from '@components/Contact.vue'
import AnimatedBackground from '@components/AnimatedBackground.vue'

const activeSection = ref('home')

// Define color schemes for gradient orbs based on active section
const sectionColors: Record<string, { orb1: string; orb2: string; orb3: string; orb4: string }> = {
  home: { 
    orb1: 'bg-blue-600/30', 
    orb2: 'bg-violet-600/25', 
    orb3: 'bg-cyan-600/20', 
    orb4: 'bg-indigo-600/20' 
  },
  services: { 
    orb1: 'bg-violet-600/30', 
    orb2: 'bg-purple-600/25', 
    orb3: 'bg-pink-600/20', 
    orb4: 'bg-fuchsia-600/20' 
  },
  skills: { 
    orb1: 'bg-cyan-600/30', 
    orb2: 'bg-blue-600/25', 
    orb3: 'bg-violet-600/20', 
    orb4: 'bg-teal-600/20' 
  },
  journey: { 
    orb1: 'bg-indigo-600/30', 
    orb2: 'bg-violet-600/25', 
    orb3: 'bg-blue-600/20', 
    orb4: 'bg-purple-600/20' 
  },
  contact: { 
    orb1: 'bg-cyan-500/30', 
    orb2: 'bg-teal-600/25', 
    orb3: 'bg-blue-600/20', 
    orb4: 'bg-emerald-600/20' 
  }
}

const colors = computed(() => sectionColors[activeSection.value] || sectionColors.home)

const { t } = useI18n()
</script>

<template>
  <div class="min-h-screen bg-slate-950 relative overflow-hidden">
    <!-- Animated particle background -->
    <AnimatedBackground :active-section="activeSection" />

    <!-- Animated background grid -->
    <div class="fixed inset-0 opacity-20">
      <div 
        class="absolute inset-0" 
        :style="{
          backgroundImage: `
            linear-gradient(rgba(59, 130, 246, 0.1) 1px, transparent 1px),
            linear-gradient(90deg, rgba(59, 130, 246, 0.1) 1px, transparent 1px)
          `,
          backgroundSize: '50px 50px',
          animation: 'gridMove 20s linear infinite'
        }"
      ></div>
    </div>

    <!-- Enhanced gradient orbs with animation - colors change based on section -->
    <div class="fixed inset-0 pointer-events-none overflow-hidden">
      <div 
        :class="`absolute top-0 left-1/4 w-[600px] h-[600px] ${colors.orb1} rounded-full blur-[140px] transition-all duration-1000`"
        style="animation: float 8s ease-in-out infinite"
      ></div>
      <div 
        :class="`absolute bottom-1/4 right-1/4 w-[700px] h-[700px] ${colors.orb2} rounded-full blur-[140px] transition-all duration-1000`"
        style="animation: float 10s ease-in-out infinite; animation-delay: 1s"
      ></div>
      <div 
        :class="`absolute top-1/2 left-1/2 w-[500px] h-[500px] ${colors.orb3} rounded-full blur-[140px] transition-all duration-1000`"
        style="animation: float 12s ease-in-out infinite; animation-delay: 2s"
      ></div>
      <div 
        :class="`absolute top-1/4 right-1/3 w-[400px] h-[400px] ${colors.orb4} rounded-full blur-[120px] transition-all duration-1000`"
        style="animation: float 9s ease-in-out infinite; animation-delay: 3s"
      ></div>
    </div>

    <!-- Geometric patterns with multiple layers -->
    <div class="fixed inset-0 pointer-events-none opacity-5">
      <svg class="w-full h-full" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <pattern id="hexagons" x="0" y="0" width="100" height="87" patternUnits="userSpaceOnUse">
            <path d="M50 0L93.3 25V75L50 100L6.7 75V25z" fill="none" stroke="currentColor" stroke-width="0.5" class="text-blue-400"/>
          </pattern>
          <pattern id="dots" x="0" y="0" width="40" height="40" patternUnits="userSpaceOnUse">
            <circle cx="20" cy="20" r="1.5" fill="currentColor" class="text-violet-400"/>
          </pattern>
        </defs>
        <rect width="100%" height="50%" fill="url(#hexagons)" />
        <rect y="50%" width="100%" height="50%" fill="url(#dots)" />
      </svg>
    </div>

    <!-- Diagonal lines overlay -->
    <div class="fixed inset-0 pointer-events-none opacity-5">
      <div 
        class="absolute inset-0" 
        :style="{
          backgroundImage: `
            repeating-linear-gradient(
              45deg,
              transparent,
              transparent 50px,
              rgba(59, 130, 246, 0.3) 50px,
              rgba(59, 130, 246, 0.3) 51px
            )
          `
        }"
      ></div>
    </div>

    <!-- Radial gradient overlay from center -->
    <div class="fixed inset-0 pointer-events-none">
      <div class="absolute inset-0 bg-gradient-radial from-transparent via-transparent to-slate-950/50"></div>
    </div>

    <Navigation 
      :active-section="activeSection" 
      @update:active-section="activeSection = $event" 
    />

    <main class="relative z-10">
      <Home v-if="activeSection === 'home'" />
      <Services v-if="activeSection === 'services'" />
      <Skills v-if="activeSection === 'skills'" />
      <Journey v-if="activeSection === 'journey'" />
      <Contact v-if="activeSection === 'contact'" />
    </main>

    <!-- Bottom branding with animated line -->
    <div class="fixed bottom-8 left-8 z-50">
      <div class="flex items-center gap-4">
        <div class="relative">
          <div class="text-2xl tracking-[0.3em] bg-gradient-to-r from-blue-400 to-violet-400 bg-clip-text text-transparent">
            Z
          </div>
          <div class="absolute -bottom-2 left-0 right-0 h-px bg-gradient-to-r from-blue-400 to-transparent"></div>
        </div>
        <div class="text-xs text-slate-500 tracking-wider">{{ t('app.branding') }}</div>
      </div>
    </div>

    <!-- Animated social sidebar -->
    <div class="fixed right-8 top-1/2 -translate-y-1/2 flex flex-col gap-6 z-50">
      <div 
        v-for="(social, index) in [
          { name: 'LinkedIn', icon: 'in' },
          { name: 'GitHub', icon: 'gh' },
          { name: 'Twitter', icon: 'tw' }
        ]" 
        :key="index" 
        class="group relative"
      >
        <div class="absolute -left-32 top-1/2 -translate-y-1/2 opacity-0 group-hover:opacity-100 transition-all duration-300 pointer-events-none">
          <div class="bg-slate-900/90 backdrop-blur border border-blue-500/50 px-4 py-2 text-sm text-blue-400 whitespace-nowrap">
            {{ social.name }}
          </div>
          <div class="absolute right-0 top-1/2 -translate-y-1/2 translate-x-full">
            <div class="w-0 h-0 border-t-8 border-b-8 border-l-8 border-transparent border-l-blue-500/50"></div>
          </div>
        </div>
        <button class="relative w-12 h-12 border border-slate-700 hover:border-blue-500 bg-slate-900/50 backdrop-blur flex items-center justify-center text-slate-500 hover:text-blue-400 transition-all group-hover:scale-110 group-hover:shadow-[0_0_20px_rgba(59,130,246,0.3)]">
          <span class="text-xs uppercase tracking-wider">{{ social.icon }}</span>
          <div class="absolute inset-0 bg-gradient-to-br from-blue-500/20 to-violet-500/20 opacity-0 group-hover:opacity-100 transition-opacity"></div>
        </button>
      </div>
    </div>
  </div>
</template>
