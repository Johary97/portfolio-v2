<script setup lang="ts">
import { ref } from 'vue'
import { Menu, Home, Briefcase, Code, X, User, Mail } from 'lucide-vue-next'

interface Props {
  activeSection: string
}

const props = defineProps<Props>()

const emit = defineEmits<{
  'update:activeSection': [section: string]
}>()

const menuOpen = ref(false)

const navItems = [
  { id: 'home', icon: Home, label: 'Accueil', number: '01' },
  { id: 'services', icon: Briefcase, label: 'Services', number: '02' },
  { id: 'skills', icon: Code, label: 'Compétences', number: '03' },
  { id: 'journey', icon: User, label: 'Parcours', number: '04' },
  { id: 'contact', icon: Mail, label: 'Contact', number: '05' },
]

const setActiveSection = (section: string) => {
  emit('update:activeSection', section)
  menuOpen.value = false
}
</script>

<template>
  <!-- Top navigation bar -->
  <div class="fixed top-0 left-0 right-0 z-50 border-b border-slate-800/50 backdrop-blur-xl bg-slate-950/80">
    <div class="flex items-center justify-between px-8 py-4">
      <!-- Logo -->
      <div class="relative group">
        <div class="flex items-center gap-3">
          <div class="w-10 h-10 border-2 border-blue-500 bg-slate-900 flex items-center justify-center relative overflow-hidden group-hover:border-violet-500 transition-colors">
            <span class="text-blue-400 text-sm tracking-wider group-hover:text-violet-400 transition-colors">JF</span>
            <div class="absolute inset-0 bg-gradient-to-br from-blue-500/20 to-violet-500/20 opacity-0 group-hover:opacity-100 transition-opacity"></div>
          </div>
          <div>
            <div class="text-sm text-white tracking-wide">Johary Fiononana</div>
            <div class="text-xs text-slate-500">Full Stack Developer</div>
          </div>
        </div>
      </div>

      <!-- Menu button -->
      <button 
        @click="menuOpen = !menuOpen"
        class="relative w-12 h-12 border border-slate-700 hover:border-blue-500 bg-slate-900/50 flex items-center justify-center text-slate-500 hover:text-blue-400 transition-all group"
      >
        <X v-if="menuOpen" class="w-5 h-5" />
        <Menu v-else class="w-5 h-5" />
        <div class="absolute inset-0 bg-gradient-to-br from-blue-500/20 to-violet-500/20 opacity-0 group-hover:opacity-100 transition-opacity"></div>
      </button>
    </div>
  </div>

  <!-- Full screen menu -->
  <div 
    :class="`fixed inset-0 z-40 bg-slate-950/98 backdrop-blur-2xl transition-all duration-500 ${
      menuOpen ? 'opacity-100 pointer-events-auto' : 'opacity-0 pointer-events-none'
    }`"
  >
    <div class="flex items-center justify-center h-full">
      <nav class="space-y-8">
        <button
          v-for="item in navItems"
          :key="item.id"
          @click="setActiveSection(item.id)"
          class="group relative block w-full text-left"
        >
          <div :class="`${
            activeSection === item.id ? 'opacity-100' : 'opacity-0 group-hover:opacity-100'
          } absolute -left-16 top-1/2 -translate-y-1/2 transition-all`">
            <div :class="`w-12 h-12 border-2 transition-all ${
              activeSection === item.id 
                ? 'border-blue-500 bg-blue-500/20' 
                : 'border-slate-700 group-hover:border-blue-400'
            } flex items-center justify-center`">
              <component 
                :is="item.icon" 
                :class="`w-5 h-5 transition-colors ${
                  activeSection === item.id ? 'text-blue-400' : 'text-slate-500 group-hover:text-blue-400'
                }`" 
              />
            </div>
          </div>
          
          <div class="flex items-center gap-6">
            <span :class="`text-7xl font-light transition-all ${
              activeSection === item.id ? 'text-blue-500' : 'text-slate-700 group-hover:text-slate-500'
            }`">
              {{ item.number }}
            </span>
            <div>
              <div class="text-xs text-slate-500 uppercase tracking-widest mb-2">Section</div>
              <div :class="`text-5xl tracking-tight transition-all ${
                activeSection === item.id ? 'text-white' : 'text-slate-600 group-hover:text-slate-500'
              }`">
                {{ item.label }}
              </div>
            </div>
          </div>

          <!-- Hover line -->
          <div :class="`w-32 h-px bg-gradient-to-r from-blue-500 to-violet-500 transition-all origin-left ${
            activeSection === item.id ? 'scale-x-100' : 'scale-x-0 group-hover:scale-x-100'
          }`"></div>
        </button>
      </nav>
    </div>

    <!-- Decorative elements -->
    <div class="absolute top-0 right-0 w-96 h-96 bg-blue-600/10 rounded-full blur-[150px] animate-pulse"></div>
    <div class="absolute bottom-0 left-0 w-96 h-96 bg-violet-600/10 rounded-full blur-[150px] animate-pulse" style="animation-delay: 1s"></div>
  </div>

  <!-- Side indicator dots -->
  <nav class="fixed left-8 top-1/2 -translate-y-1/2 z-30 flex flex-col gap-6">
    <button
      v-for="item in navItems"
      :key="item.id"
      @click="setActiveSection(item.id)"
      class="group flex items-center gap-4"
    >
      <div class="relative">
        <div :class="`w-3 h-3 border-2 transition-all ${
          activeSection === item.id 
            ? 'border-blue-500 bg-blue-500 scale-125' 
            : 'border-slate-600 group-hover:border-blue-400 group-hover:scale-110'
        }`">
          <div v-if="activeSection === item.id" class="absolute inset-0 bg-blue-500 animate-ping"></div>
        </div>
      </div>
      <div :class="`text-xs text-slate-500 uppercase tracking-widest whitespace-nowrap transition-all opacity-0 -translate-x-2 group-hover:opacity-100 group-hover:translate-x-0 ${
        activeSection === item.id ? 'text-blue-400' : ''
      }`">
        {{ item.label }}
      </div>
    </button>
  </nav>
</template>
