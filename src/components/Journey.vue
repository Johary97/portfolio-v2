<script setup lang="ts">
import { Briefcase, GraduationCap, Calendar, MapPin, Award } from 'lucide-vue-next'

const experiences = [
  {
    period: '2021 - Présent',
    title: 'Senior Full Stack Developer',
    company: 'Tech Solutions Inc.',
    location: 'Remote',
    description: "Développement d'applications web et mobiles complexes utilisant React, Laravel et AWS. Leadership technique et mentorat d'une équipe de 5 développeurs.",
    achievements: [
      'Augmentation de 40% des performances des applications',
      'Mise en place de CI/CD réduisant le temps de déploiement de 60%',
      'Formation de 3 développeurs juniors'
    ],
    color: 'blue'
  },
  {
    period: '2019 - 2021',
    title: 'Full Stack Developer',
    company: 'Digital Agency',
    location: 'Antananarivo',
    description: 'Conception et développement de solutions web sur mesure pour divers clients. Spécialisation en React et Laravel.',
    achievements: [
      '15+ projets livrés avec succès',
      'Satisfaction client à 95%',
      'Réduction des coûts de maintenance de 30%'
    ],
    color: 'cyan'
  },
  {
    period: '2017 - 2019',
    title: 'Junior Developer',
    company: 'StartUp Co.',
    location: 'Antananarivo',
    description: 'Développement frontend et backend. Apprentissage des meilleures pratiques et des technologies modernes.',
    achievements: [
      'Développement de 10+ features majeures',
      'Participation à l\'architecture de 3 nouveaux projets',
      'Obtention de certifications AWS et React'
    ],
    color: 'violet'
  }
]

const education = [
  {
    period: '2014 - 2017',
    degree: 'Licence en Informatique',
    school: 'Université d\'Antananarivo',
    description: 'Spécialisation en développement web et ingénierie logicielle',
    achievements: [
      'Major de promotion',
      'Projet de fin d\'études primé',
      'Stage de 6 mois en entreprise'
    ]
  }
]

const certifications = [
  { name: 'AWS Certified Solutions Architect', year: '2021' },
  { name: 'React Advanced Certification', year: '2020' },
  { name: 'Laravel Certified Developer', year: '2019' }
]
</script>

<template>
  <div class="min-h-screen px-8 md:px-16 lg:px-24 py-32">
    <div class="max-w-7xl mx-auto">
      <!-- Header -->
      <div class="mb-20 text-center relative">
        <div class="inline-flex items-center gap-3 border border-blue-500/30 bg-blue-500/10 backdrop-blur px-4 py-2 mb-6">
          <div class="w-2 h-2 bg-blue-400 rotate-45"></div>
          <span class="text-sm text-blue-400 tracking-[0.3em] uppercase">Mon histoire</span>
        </div>
        
        <h2 class="text-6xl lg:text-7xl tracking-tight mb-6">
          <span class="bg-gradient-to-r from-white via-blue-100 to-white bg-clip-text text-transparent">
            Mon Parcours
          </span>
        </h2>
        
        <div class="flex items-center gap-2 mb-6 justify-center">
          <div class="w-24 h-px bg-gradient-to-r from-transparent via-blue-500 to-transparent"></div>
          <div class="w-2 h-2 bg-blue-500 rotate-45"></div>
          <div class="w-24 h-px bg-gradient-to-r from-transparent via-blue-500 to-transparent"></div>
        </div>

        <p class="text-xl text-slate-300 max-w-2xl mx-auto leading-relaxed">
          Une évolution constante à travers différentes expériences et projets qui ont forgé mon expertise technique.
        </p>
      </div>

      <div class="grid lg:grid-cols-2 gap-16">
        <!-- Experiences Professionnelles -->
        <div>
          <div class="flex items-center gap-4 mb-12">
            <div class="w-14 h-14 border-2 border-blue-500 bg-blue-500/10 flex items-center justify-center">
              <Briefcase class="w-7 h-7 text-blue-400" />
            </div>
            <h3 class="text-3xl text-white">Expériences Professionnelles</h3>
          </div>

          <div class="relative space-y-12">
            <!-- Vertical timeline line -->
            <div class="absolute left-0 top-0 bottom-0 w-px bg-gradient-to-b from-blue-500 via-cyan-500 to-transparent"></div>

            <div
              v-for="(exp, index) in experiences"
              :key="index"
              class="relative pl-12 group"
            >
              <!-- Timeline dot -->
              <div class="absolute left-0 top-0 w-3 h-3 -translate-x-[5px]">
                <div class="w-full h-full border-2 border-blue-500 bg-slate-950 rotate-45 group-hover:scale-150 group-hover:bg-blue-500 transition-all"></div>
                <div class="absolute inset-0 border-2 border-blue-500 bg-blue-500 rotate-45 opacity-0 group-hover:opacity-100 animate-ping"></div>
              </div>

              <!-- Content card -->
              <div class="border border-slate-800 bg-slate-900/30 backdrop-blur p-6 hover:border-blue-500/50 transition-all group-hover:translate-x-2">
                <!-- Period badge -->
                <div class="flex items-center gap-2 text-sm text-cyan-400 mb-3">
                  <Calendar class="w-4 h-4" />
                  <span>{{ exp.period }}</span>
                </div>

                <!-- Title -->
                <h4 class="text-xl text-white mb-2 group-hover:text-blue-400 transition-colors">
                  {{ exp.title }}
                </h4>

                <!-- Company -->
                <div class="flex items-center gap-2 text-slate-400 mb-1">
                  <Briefcase class="w-4 h-4" />
                  <span>{{ exp.company }}</span>
                </div>

                <!-- Location -->
                <div class="flex items-center gap-2 text-slate-500 mb-4 text-sm">
                  <MapPin class="w-4 h-4" />
                  <span>{{ exp.location }}</span>
                </div>

                <!-- Description -->
                <p class="text-slate-300 text-sm mb-4 leading-relaxed">
                  {{ exp.description }}
                </p>

                <!-- Achievements -->
                <div class="space-y-2">
                  <div
                    v-for="(achievement, i) in exp.achievements"
                    :key="i"
                    class="flex items-start gap-2 text-sm text-slate-300"
                  >
                    <div class="w-1 h-1 bg-blue-400 mt-2 rounded-full"></div>
                    <span>{{ achievement }}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Formation & Certifications -->
        <div>
          <div class="flex items-center gap-4 mb-12">
            <div class="w-14 h-14 border-2 border-violet-500 bg-violet-500/10 flex items-center justify-center">
              <GraduationCap class="w-7 h-7 text-violet-400" />
            </div>
            <h3 class="text-3xl text-white">Formation</h3>
          </div>

          <!-- Education -->
          <div class="space-y-8 mb-12">
            <div
              v-for="(edu, index) in education"
              :key="index"
              class="border border-slate-800 bg-slate-900/30 backdrop-blur p-6 hover:border-violet-500/50 transition-all"
            >
              <div class="flex items-center gap-2 text-sm text-violet-400 mb-3">
                <Calendar class="w-4 h-4" />
                <span>{{ edu.period }}</span>
              </div>

              <h4 class="text-xl text-white mb-2">{{ edu.degree }}</h4>
              <p class="text-slate-400 mb-4">{{ edu.school }}</p>
              <p class="text-slate-300 text-sm mb-4">{{ edu.description }}</p>

              <div class="space-y-2">
                <div
                  v-for="(achievement, i) in edu.achievements"
                  :key="i"
                  class="flex items-start gap-2 text-sm text-slate-300"
                >
                  <div class="w-1 h-1 bg-violet-400 mt-2 rounded-full"></div>
                  <span>{{ achievement }}</span>
                </div>
              </div>
            </div>
          </div>

          <!-- Certifications -->
          <div class="flex items-center gap-4 mb-8">
            <div class="w-14 h-14 border-2 border-cyan-500 bg-cyan-500/10 flex items-center justify-center">
              <Award class="w-7 h-7 text-cyan-400" />
            </div>
            <h3 class="text-3xl text-white">Certifications</h3>
          </div>

          <div class="space-y-4">
            <div
              v-for="(cert, index) in certifications"
              :key="index"
              class="group flex items-center justify-between border border-slate-800 bg-slate-900/30 backdrop-blur p-4 hover:border-cyan-500/50 transition-all"
            >
              <div class="flex items-center gap-3">
                <div class="w-10 h-10 border border-cyan-500/30 bg-cyan-500/10 flex items-center justify-center group-hover:bg-cyan-500/20 transition-all">
                  <Award class="w-5 h-5 text-cyan-400" />
                </div>
                <span class="text-white">{{ cert.name }}</span>
              </div>
              <span class="text-slate-500 text-sm">{{ cert.year }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
