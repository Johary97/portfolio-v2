<script setup lang="ts">
import { Cloud, Code, Server, Database, Zap, Lock, Layout } from 'lucide-vue-next'

const services = [
  {
    icon: Cloud,
    title: 'Solutions Cloud',
    description: "Architecture cloud scalable et sécurisée sur AWS avec déploiement automatisé et monitoring en temps réel",
    tags: ['AWS', 'Cloud Infrastructure', 'DevOps', 'CI/CD'],
    color: 'blue',
    number: '01'
  },
  {
    icon: Code,
    title: 'Développement Web',
    description: 'Applications web modernes et performantes avec React, Next.js et les dernières technologies frontend',
    tags: ['React', 'Next.js', 'TypeScript', 'Tailwind'],
    color: 'violet',
    number: '02'
  },
  {
    icon: Server,
    title: 'Architecture Backend',
    description: "Conception d'APIs RESTful robustes et microservices avec Laravel, Symfony et Node.js",
    tags: ['Laravel', 'Symfony', 'Node.js', 'API REST'],
    color: 'cyan',
    number: '03'
  },
  {
    icon: Database,
    title: 'Bases de Données',
    description: 'Modélisation et optimisation de bases de données relationnelles et NoSQL pour performances maximales',
    tags: ['PostgreSQL', 'MongoDB', 'Redis', 'Optimization'],
    color: 'indigo',
    number: '04'
  }
]

const features = [
  { icon: Zap, label: 'Performance optimale', color: 'yellow' },
  { icon: Lock, label: 'Sécurité renforcée', color: 'green' },
  { icon: Layout, label: 'Design responsive', color: 'blue' },
  { icon: Server, label: 'Infrastructure scalable', color: 'purple' }
]
</script>

<template>
  <div class="min-h-screen px-8 md:px-16 lg:px-24 py-32">
    <div class="max-w-7xl mx-auto">
      <!-- Header with decorative elements -->
      <div class="mb-20 relative">
        <div class="flex items-start gap-8">
          <div class="flex-1">
            <div class="inline-flex items-center gap-3 border border-blue-500/30 bg-blue-500/10 backdrop-blur px-4 py-2 mb-6">
              <div class="w-2 h-2 bg-blue-400 rotate-45"></div>
              <span class="text-sm text-blue-400 tracking-[0.3em] uppercase">Ce que je propose</span>
            </div>
            
            <h2 class="text-6xl lg:text-7xl tracking-tight mb-6">
              <span class="bg-gradient-to-r from-white via-blue-100 to-white bg-clip-text text-transparent">
                Mes Services
              </span>
            </h2>
            
            <div class="flex items-center gap-2 mb-6">
              <div class="w-24 h-px bg-gradient-to-r from-blue-500 via-violet-500 to-transparent"></div>
              <div class="w-2 h-2 bg-violet-500 rotate-45"></div>
            </div>

            <p class="text-xl text-slate-300/85 max-w-2xl leading-relaxed">
              Des solutions complètes et sur mesure pour transformer vos idées en applications 
              performantes et évolutives qui répondent aux exigences les plus élevées.
            </p>
          </div>

          <!-- Features grid -->
          <div class="grid grid-cols-2 gap-3 mt-12">
            <div
              v-for="(feature, index) in features"
              :key="index"
              class="border border-slate-800 bg-slate-900/30 backdrop-blur p-4 hover:border-blue-500/50 transition-all group"
            >
              <component :is="feature.icon" class="w-5 h-5 text-blue-400 mb-2 group-hover:scale-110 transition-transform" />
              <div class="text-xs text-slate-300">{{ feature.label }}</div>
            </div>
          </div>
        </div>
      </div>

      <!-- Services Grid -->
      <div class="grid md:grid-cols-2 gap-8 mb-20">
        <div
          v-for="(service, index) in services"
          :key="index"
          class="group relative border border-slate-800 bg-slate-900/30 backdrop-blur overflow-hidden hover:border-blue-500/50 transition-all duration-500"
        >
          <!-- Number watermark -->
          <!-- <div class="absolute top-4 right-4 text-8xl opacity-5 group-hover:opacity-10 transition-opacity">
            {{ service.number }}
          </div> -->

          <div class="relative p-8">
            <!-- Icon with animated border -->
            <div class="relative inline-flex mb-6">
              <div :class="`w-16 h-16 border-2 border-${service.color}-500/50 bg-${service.color}-500/10 flex items-center justify-center group-hover:border-${service.color}-500 transition-all`">
                <component :is="service.icon" :class="`w-8 h-8 text-${service.color}-400 group-hover:scale-110 transition-transform`" />
              </div>
              <!-- Animated corner accents -->
              <div :class="`absolute -top-1 -left-1 w-3 h-3 border-t-2 border-l-2 border-${service.color}-500 opacity-0 group-hover:opacity-100 transition-opacity`"></div>
              <div :class="`absolute -bottom-1 -right-1 w-3 h-3 border-b-2 border-r-2 border-${service.color}-500 opacity-0 group-hover:opacity-100 transition-opacity`"></div>
            </div>

            <!-- Number badge -->
            <div class="inline-block border border-slate-800 bg-slate-900/50 px-3 py-1 text-xs text-slate-500 tracking-widest mb-4">
              {{ service.number }}
            </div>

            <!-- Title -->
            <h3 class="text-3xl text-white mb-4 group-hover:text-transparent group-hover:bg-gradient-to-r group-hover:from-blue-400 group-hover:to-violet-400 group-hover:bg-clip-text transition-all">
              {{ service.title }}
            </h3>
            
            <!-- Description -->
            <p class="text-slate-300 mb-6 leading-relaxed">
              {{ service.description }}
            </p>

            <!-- Tags -->
            <div class="flex flex-wrap gap-2 mb-6">
              <span
                v-for="(tag, i) in service.tags"
                :key="i"
                class="px-3 py-1 border border-slate-600 bg-slate-900/50 text-slate-300 text-xs hover:border-blue-500/50 hover:text-blue-400 transition-all cursor-pointer"
              >
                {{ tag }}
              </span>
            </div>

            <!-- Learn more link -->
            <div class="flex items-center gap-2 text-blue-400 opacity-0 group-hover:opacity-100 transition-all group-hover:translate-x-2">
              <span class="text-sm tracking-wider uppercase">Découvrir</span>
              <div class="w-12 h-px bg-gradient-to-r from-blue-500 to-transparent"></div>
            </div>
          </div>

          <!-- Animated accent line -->
          <div :class="`absolute top-0 left-0 right-0 h-1 bg-gradient-to-r from-${service.color}-500 to-transparent transform origin-left scale-x-0 group-hover:scale-x-100 transition-transform duration-500`"></div>
          <div :class="`absolute bottom-0 left-0 right-0 h-1 bg-gradient-to-l from-${service.color}-500 to-transparent transform origin-right scale-x-0 group-hover:scale-x-100 transition-transform duration-500`"></div>
        </div>
      </div>

      <!-- CTA Section -->
      <div class="group relative border-2 border-slate-800 bg-slate-900/30 backdrop-blur p-16 hover:border-blue-500/50 transition-all text-center overflow-hidden">
        <div class="relative z-10">
          <h3 class="text-4xl text-white mb-4">
            <span class="bg-gradient-to-r from-blue-400 to-violet-400 bg-clip-text text-transparent">
              Prêt à démarrer votre projet ?
            </span>
          </h3>
          
          <p class="text-slate-300 mb-8 max-w-2xl mx-auto text-lg">
            Discutons ensemble de votre projet et transformons vos idées en réalité digitale.
            Je suis prêt à relever de nouveaux défis.
          </p>

          <div class="flex flex-wrap gap-4 justify-center">
            <button class="group/btn relative px-8 py-4 border-2 border-blue-500 bg-blue-500 text-white overflow-hidden hover:border-blue-400 transition-all">
              <span class="relative z-10 flex items-center gap-2 tracking-wider uppercase text-sm">
                Démarrer un projet
                <div class="w-5 h-5 border border-white rounded-full flex items-center justify-center group-hover/btn:rotate-90 transition-transform">
                  <div class="w-1.5 h-1.5 bg-white rounded-full"></div>
                </div>
              </span>
              <div class="absolute inset-0 bg-gradient-to-r from-blue-600 to-violet-600 opacity-0 group-hover/btn:opacity-100 transition-opacity"></div>
            </button>

            <button class="group/btn relative px-8 py-4 border-2 border-slate-700 bg-transparent text-white overflow-hidden hover:border-blue-500 transition-all">
              <span class="relative z-10 tracking-wider uppercase text-sm">
                Planifier un appel
              </span>
              <div class="absolute inset-0 bg-blue-500/10 opacity-0 group-hover/btn:opacity-100 transition-opacity"></div>
            </button>
          </div>
        </div>

        <!-- Floating decorative elements -->
        <div class="absolute top-12 right-12 w-16 h-16 border border-blue-500/20 rotate-45 group-hover:rotate-90 transition-transform duration-700"></div>
        <div class="absolute bottom-12 left-12 w-12 h-12 border border-violet-500/20 rotate-45 group-hover:-rotate-90 transition-transform duration-700"></div>
      </div>
    </div>
  </div>
</template>
