<script setup lang="ts">
import { ref } from 'vue'
import { useI18n } from 'vue-i18n'
import { Code2, Database, Globe, Boxes, FolderKanban, Users, Target, ArrowRight, Lightbulb } from 'lucide-vue-next'

const { t } = useI18n()

const activeTab = ref('projects')

const projects = [
  {
    icon: Target,
    titleKey: 'skills.projects.ecommerce.title',
    solutionKey: 'skills.projects.ecommerce.solution',
    resultsKey: 'skills.projects.ecommerce.results',
    techStack: ['React', 'Node.js', 'PostgreSQL', 'AWS', 'Stripe'],
    durationKey: 'skills.projects.ecommerce.duration',
    teamKey: 'skills.projects.ecommerce.team',
    number: '01'
  },
  {
    icon: Users,
    titleKey: 'skills.projects.saas.title',
    solutionKey: 'skills.projects.saas.solution',
    resultsKey: 'skills.projects.saas.results',
    techStack: ['Next.js', 'Laravel', 'MySQL', 'Redis', 'Docker'],
    durationKey: 'skills.projects.saas.duration',
    teamKey: 'skills.projects.saas.team',
    number: '02'
  },
  {
    icon: FolderKanban,
    titleKey: 'skills.projects.dataviz.title',
    solutionKey: 'skills.projects.dataviz.solution',
    resultsKey: 'skills.projects.dataviz.results',
    techStack: ['Python', 'Scrapy', 'D3.js', 'Node.js', 'MongoDB'],
    durationKey: 'skills.projects.dataviz.duration',
    teamKey: 'skills.projects.dataviz.team',
    number: '03'
  }
]

const skillCategories = [
  {
    icon: Code2,
    titleKey: 'skills.categories.frontend',
    gradient: 'from-blue-500 to-cyan-500',
    skills: ['React', 'Vue.js', 'Next.js', 'TypeScript', 'Tailwind CSS']
  },
  {
    icon: Database,
    titleKey: 'skills.categories.backend',
    gradient: 'from-violet-500 to-purple-500',
    skills: ['Laravel', 'Symfony', 'Node.js', 'Python', 'PostgreSQL']
  },
  {
    icon: Globe,
    titleKey: 'skills.categories.devops',
    gradient: 'from-cyan-500 to-teal-500',
    skills: ['AWS', 'Docker', 'CI/CD', 'Git', 'Linux']
  },
  {
    icon: Boxes,
    titleKey: 'skills.categories.architecture',
    gradient: 'from-indigo-500 to-blue-500',
    skills: ['Microservices', 'REST API', 'GraphQL', 'Design Patterns', 'System Design']
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
          <span class="text-sm text-violet-400 tracking-[0.3em] uppercase">{{ t('skills.badge') }}</span>
        </div>

        <h2 class="text-6xl lg:text-7xl tracking-tight mb-6">
          <span class="bg-gradient-to-r from-white via-violet-100 to-white bg-clip-text text-transparent">
            {{ t('skills.title') }}
          </span>
        </h2>

        <div class="flex items-center gap-2 mb-6">
          <div class="w-24 h-px bg-gradient-to-r from-violet-500 via-blue-500 to-transparent"></div>
          <div class="w-2 h-2 bg-blue-500 rotate-45"></div>
        </div>

        <p class="text-xl text-slate-300 max-w-2xl leading-relaxed">
          {{ t('skills.description') }}
        </p>
      </div>

      <!-- Tabs -->
      <div class="flex gap-4 mb-12 border-b border-slate-800">
        <button
          @click="activeTab = 'projects'"
          :class="`relative px-6 py-3 text-sm tracking-wider uppercase transition-all ${
            activeTab === 'projects'
              ? 'text-violet-400'
              : 'text-slate-500 hover:text-slate-300'
          }`"
        >
          {{ t('skills.tabProjects') }}
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
          {{ t('skills.tabSkills') }}
          <div
            v-if="activeTab === 'skills'"
            class="absolute bottom-0 left-0 right-0 h-px bg-gradient-to-r from-violet-500 to-blue-500"
          ></div>
        </button>
      </div>

      <!-- Approach / Methodology Scenarios -->
      <div v-if="activeTab === 'projects'" class="space-y-8 mb-20">
        <div class="grid lg:grid-cols-3 gap-8">
          <div
            v-for="(project, index) in projects"
            :key="index"
            class="group relative border border-slate-800 bg-slate-900/30 backdrop-blur overflow-hidden hover:border-violet-500/50 transition-all"
          >
            <div class="p-8">
              <!-- Scenario indicator -->
              <div class="flex items-center gap-2 mb-4">
                <Lightbulb class="w-4 h-4 text-violet-400" />
                <span class="text-xs text-violet-400 uppercase tracking-wider">{{ t('skills.solutionLabel') }}</span>
              </div>

              <h3 class="text-2xl text-white mb-4 group-hover:text-violet-400 transition-colors">
                {{ t(project.titleKey) }}
              </h3>

              <!-- Solution -->
              <div class="mb-4">
                <p class="text-slate-300 leading-relaxed text-sm">
                  {{ t(project.solutionKey) }}
                </p>
              </div>

              <!-- Expected results -->
              <div class="mb-6 border-l-2 border-blue-500/30 pl-4">
                <div class="text-xs text-blue-400 uppercase tracking-wider mb-2 flex items-center gap-1">
                  <ArrowRight class="w-3 h-3" />
                  {{ t('skills.resultsLabel') }}
                </div>
                <p class="text-blue-300/80 text-sm leading-relaxed">
                  {{ t(project.resultsKey) }}
                </p>
              </div>

              <!-- Tech Stack -->
              <div class="flex flex-wrap gap-2 mb-6">
                <span
                  v-for="(tech, i) in project.techStack"
                  :key="i"
                  class="px-3 py-1 border border-slate-600 bg-slate-900/50 text-slate-300 text-xs hover:border-violet-500/50 hover:text-violet-400 transition-all cursor-default"
                >
                  {{ tech }}
                </span>
              </div>

              <!-- Stats -->
              <div class="grid grid-cols-2 gap-4 pt-4 border-t border-slate-800">
                <div>
                  <div class="text-2xl text-blue-400 mb-1">{{ t(project.durationKey) }}</div>
                  <div class="text-xs text-slate-300 uppercase tracking-wider">{{ t('skills.durationLabel') }}</div>
                </div>
                <div>
                  <div class="text-2xl text-violet-400 mb-1">{{ t(project.teamKey) }}</div>
                  <div class="text-xs text-slate-300 uppercase tracking-wider">{{ t('skills.teamLabel') }}</div>
                </div>
              </div>
            </div>

            <!-- Animated accent lines -->
            <div class="absolute top-0 left-0 right-0 h-1 bg-gradient-to-r from-blue-500 via-violet-500 to-transparent transform origin-left scale-x-0 group-hover:scale-x-100 transition-transform duration-700"></div>
          </div>
        </div>

        <!-- CTA Placeholder card -->
        <div class="group relative border-2 border-dashed border-slate-700 bg-slate-900/20 backdrop-blur p-12 hover:border-violet-500/50 transition-all text-center overflow-hidden">
          <div class="relative z-10">
            <h3 class="text-3xl text-white mb-3">
              <span class="bg-gradient-to-r from-violet-400 to-blue-400 bg-clip-text text-transparent">
                {{ t('skills.ctaPlaceholder') }}
              </span>
            </h3>
            <p class="text-slate-400 mb-6 max-w-lg mx-auto">
              {{ t('skills.ctaPlaceholderSub') }}
            </p>
            <button class="group/btn relative px-8 py-4 border-2 border-violet-500 bg-violet-500 text-white overflow-hidden hover:border-violet-400 transition-all">
              <span class="relative z-10 flex items-center gap-2 tracking-wider uppercase text-sm">
                {{ t('skills.ctaPlaceholderBtn') }}
                <ArrowRight class="w-4 h-4 group-hover/btn:translate-x-1 transition-transform" />
              </span>
              <div class="absolute inset-0 bg-gradient-to-r from-violet-600 to-blue-600 opacity-0 group-hover/btn:opacity-100 transition-opacity"></div>
            </button>
          </div>
          <div class="absolute top-8 right-8 w-12 h-12 border border-violet-500/20 rotate-45 group-hover:rotate-90 transition-transform duration-700"></div>
          <div class="absolute bottom-8 left-8 w-8 h-8 border border-blue-500/20 rotate-45 group-hover:-rotate-90 transition-transform duration-700"></div>
        </div>
      </div>

      <!-- Skills Grid - Tech tags -->
      <div v-if="activeTab === 'skills'" class="space-y-16">
        <div class="grid md:grid-cols-2 gap-8">
          <div
            v-for="(category, index) in skillCategories"
            :key="index"
            class="group relative border border-slate-800 bg-slate-900/30 backdrop-blur p-8 hover:border-blue-500/50 transition-all"
          >
            <div class="flex items-center gap-4 mb-8">
              <div :class="`w-14 h-14 border-2 border-slate-700 bg-gradient-to-br ${category.gradient} bg-clip-border flex items-center justify-center group-hover:border-transparent transition-all`">
                <component :is="category.icon" class="w-7 h-7 text-white" />
              </div>
              <h3 class="text-2xl text-white">
                {{ t(category.titleKey) }}
              </h3>
            </div>

            <div class="flex flex-wrap gap-3">
              <span
                v-for="(skill, i) in category.skills"
                :key="i"
                class="px-4 py-2 border border-slate-600 bg-slate-900/50 text-slate-300 text-sm hover:border-blue-500/50 hover:text-blue-400 transition-all cursor-default"
              >
                {{ skill }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
