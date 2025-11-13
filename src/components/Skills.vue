<script setup lang="ts">
import { ref } from 'vue'
import { Code2, Database, Globe, Boxes, FolderKanban, Users, Target } from 'lucide-vue-next'

const activeTab = ref('projects')

const projects = [
  {
    icon: Target,
    title: 'E-Commerce Platform',
    description: "Plateforme complète avec panier d'achat, gestion des paiements et tableau de bord administrateur. Optimisée pour les performances et la conversion.",
    image: null,
    techStack: ['React', 'Node.js', 'PostgreSQL', 'AWS', 'Stripe'],
    stats: { duration: '4 mois', team: '3 personnes' },
    number: '01'
  },
  {
    icon: Users,
    title: 'SaaS Dashboard',
    description: "Application SaaS multi-tenant avec analytics en temps réel, gestion d'équipes et API robuste pour intégrations tierces.",
    image: null,
    techStack: ['Next.js', 'Laravel', 'MySQL', 'Redis', 'Docker'],
    stats: { duration: '6 mois', team: '4 personnes' },
    number: '02'
  },
  {
    icon: FolderKanban,
    title: 'Data Visualization Tool',
    description: "Outil de visualisation de données complexes avec graphiques interactifs. Intégration avec multiples sources de données et API pour une vue d'ensemble complète.",
    image: null,
    techStack: ['React', 'TypeScript', 'D3.js', 'Node.js', 'MongoDB'],
    stats: { duration: '5 mois', team: '5 personnes' },
    number: '03'
  }
]

const skillCategories = [
  {
    icon: Code2,
    title: 'Frontend Development',
    gradient: 'from-blue-500 to-cyan-500',
    skills: [
      { name: 'React', level: 95 },
      { name: 'Vue.js', level: 85 },
      { name: 'Next.js', level: 90 },
      { name: 'TypeScript', level: 88 },
      { name: 'Tailwind CSS', level: 92 }
    ]
  },
  {
    icon: Database,
    title: 'Backend Development',
    gradient: 'from-violet-500 to-purple-500',
    skills: [
      { name: 'Laravel', level: 90 },
      { name: 'Symfony', level: 88 },
      { name: 'Node.js', level: 85 },
      { name: 'Python', level: 82 },
      { name: 'PostgreSQL', level: 87 }
    ]
  },
  {
    icon: Globe,
    title: 'DevOps & Cloud',
    gradient: 'from-cyan-500 to-teal-500',
    skills: [
      { name: 'AWS', level: 80 },
      { name: 'Docker', level: 85 },
      { name: 'CI/CD', level: 82 },
      { name: 'Git', level: 93 },
      { name: 'Linux', level: 86 }
    ]
  },
  {
    icon: Boxes,
    title: 'Architecture & Design',
    gradient: 'from-indigo-500 to-blue-500',
    skills: [
      { name: 'Microservices', level: 78 },
      { name: 'REST API', level: 92 },
      { name: 'GraphQL', level: 75 },
      { name: 'Design Patterns', level: 85 },
      { name: 'System Design', level: 80 }
    ]
  }
]
</script>

<template>
  <div class="min-h-screen px-8 md:px-16 lg:px-24 py-32">
    <div class="max-w-7xl mx-auto">
      <!-- Header -->
      <div class="mb-20 relative">
        <div class="inline-flex items-center gap-3 border border-violet-500/30 bg-violet-500/10 backdrop-blur px-4 py-2 mb-6">
          <div class="w-2 h-2 bg-violet-400 rotate-45"></div>
          <span class="text-sm text-violet-400 tracking-[0.3em] uppercase">Mon expertise</span>
        </div>
        
        <h2 class="text-6xl lg:text-7xl tracking-tight mb-6">
          <span class="bg-gradient-to-r from-white via-violet-100 to-white bg-clip-text text-transparent">
            Compétences
          </span>
        </h2>
        
        <div class="flex items-center gap-2 mb-6">
          <div class="w-24 h-px bg-gradient-to-r from-violet-500 via-blue-500 to-transparent"></div>
          <div class="w-2 h-2 bg-blue-500 rotate-45"></div>
        </div>

        <p class="text-xl text-slate-300 max-w-2xl leading-relaxed">
          Une expertise technique complète pour concevoir et développer des solutions 
          robustes et innovantes adaptées à vos besoins.
        </p>
      </div>

      <!-- Tabs -->
      <div class="flex gap-4 mb-12 border-b border-slate-800">
        <button
          @click="activeTab = 'projects'"
          :class="`relative px-6 py-3 text-sm tracking-wider uppercase transition-all ${
            activeTab === 'projects' 
              ? 'text-violet-400' 
              : 'text-slate-500 hover:text-slate-500'
          }`"
        >
          Projets Réalisés
          <div
            v-if="activeTab === 'projects'"
            class="absolute bottom-0 left-0 right-0 h-px bg-gradient-to-r from-violet-500 to-blue-500"
          ></div>
        </button>
        <button
          @click="activeTab = 'skills'"
          :class="`relative px-6 py-3 text-sm tracking-wider uppercase transition-all ${
            activeTab === 'skills' 
              ? 'text-violet-400' 
              : 'text-slate-400 hover:text-slate-300'
          }`"
        >
          Compétences Techniques
          <div
            v-if="activeTab === 'skills'"
            class="absolute bottom-0 left-0 right-0 h-px bg-gradient-to-r from-violet-500 to-blue-500"
          ></div>
        </button>
      </div>

      <!-- Projects Grid -->
      <div v-if="activeTab === 'projects'" class="grid lg:grid-cols-3 gap-8 mb-20">
        <div
          v-for="(project, index) in projects"
          :key="index"
          class="group relative border border-slate-800 bg-slate-900/30 backdrop-blur overflow-hidden hover:border-violet-500/50 transition-all"
        >
          <!-- Project content -->
          <div class="p-8">

            <h3 class="text-2xl text-white mb-4 group-hover:text-violet-400 transition-colors">
              {{ project.title }}
            </h3>

            <p class="text-slate-300 mb-6 leading-relaxed text-sm">
              {{ project.description }}
            </p>

            <!-- Tech Stack -->
            <div class="flex flex-wrap gap-2 mb-6">
              <span
                v-for="(tech, i) in project.techStack"
                :key="i"
                class="px-3 py-1 border border-slate-600 bg-slate-900/50 text-slate-300 text-xs hover:border-violet-500/50 hover:text-violet-400 transition-all cursor-pointer"
              >
                {{ tech }}
              </span>
            </div>

            <!-- Stats -->
            <div class="grid grid-cols-2 gap-4 pt-4 border-t border-slate-800">
              <div>
                <div class="text-2xl text-blue-400 mb-1">{{ project.stats.duration }}</div>
                <div class="text-xs text-slate-300 uppercase tracking-wider">Durée</div>
              </div>
              <div>
                <div class="text-2xl text-violet-400 mb-1">{{ project.stats.team }}</div>
                <div class="text-xs text-slate-300 uppercase tracking-wider">Équipe</div>
              </div>
            </div>
          </div>

          <!-- Animated accent lines -->
          <div class="absolute top-0 left-0 right-0 h-1 bg-gradient-to-r from-blue-500 via-violet-500 to-transparent transform origin-left scale-x-0 group-hover:scale-x-100 transition-transform duration-700"></div>
        </div>
      </div>

      <!-- Skills Grid -->
      <div v-if="activeTab === 'skills'" class="space-y-16">
        <!-- Skill categories -->
        <div class="grid md:grid-cols-2 gap-8">
          <div
            v-for="(category, index) in skillCategories"
            :key="index"
            class="group border border-slate-800 bg-slate-900/30 backdrop-blur p-8 hover:border-blue-500/50 transition-all"
          >
            <!-- Header -->
            <div class="flex items-center gap-4 mb-8">
              <div :class="`w-14 h-14 border-2 border-slate-700 bg-gradient-to-br ${category.gradient} bg-clip-border flex items-center justify-center group-hover:border-transparent transition-all`">
                <component :is="category.icon" class="w-7 h-7 text-white" />
              </div>
              <h3 class="text-2xl text-white">
                {{ category.title }}
              </h3>
            </div>

            <!-- Skills with progress bars -->
            <div class="space-y-5">
              <div v-for="(skill, i) in category.skills" :key="i">
                <div class="flex justify-between mb-2">
                  <span class="text-slate-300">{{ skill.name }}</span>
                  <span :class="`bg-gradient-to-r ${category.gradient} bg-clip-text text-transparent`">
                    {{ skill.level }}%
                  </span>
                </div>
                <div class="h-2 bg-slate-800 overflow-hidden">
                  <div 
                    :class="`h-full bg-gradient-to-r ${category.gradient} transition-all duration-1000 relative overflow-hidden`"
                    :style="{ width: `${skill.level}%` }"
                  >
                    <!-- Shimmer effect -->
                    <div class="absolute inset-0 bg-gradient-to-r from-transparent via-white/20 to-transparent animate-pulse"></div>
                  </div>
                </div>
              </div>
            </div>

            <!-- Decorative corner -->
            <div class="absolute bottom-4 right-4 w-8 h-8 border-r-2 border-b-2 border-slate-800 group-hover:border-blue-500/50 transition-all"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
