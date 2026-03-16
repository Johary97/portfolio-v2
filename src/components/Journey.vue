<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import { Compass, Heart, Users, UserCircle, Network, Sparkles } from 'lucide-vue-next'

const { t } = useI18n()

const missionKeys = ['problem', 'promise', 'approach'] as const
const valueKeys = ['transparency', 'quality', 'agility', 'impact'] as const
const networkKeys = ['uiux', 'devops', 'data'] as const
</script>

<template>
  <div class="min-h-screen px-8 md:px-16 lg:px-24 py-32">
    <div class="max-w-7xl mx-auto">
      <!-- Header -->
      <div class="mb-20 text-center relative">
        <div class="inline-flex items-center gap-3 border border-blue-500/30 bg-blue-500/10 backdrop-blur px-4 py-2 mb-6">
          <div class="w-2 h-2 bg-blue-400 rotate-45"></div>
          <span class="text-sm text-blue-400 tracking-[0.3em] uppercase">{{ t('journey.badge') }}</span>
        </div>

        <h2 class="text-6xl lg:text-7xl tracking-tight mb-6">
          <span class="bg-gradient-to-r from-white via-blue-100 to-white bg-clip-text text-transparent">
            {{ t('journey.title') }}
          </span>
        </h2>

        <div class="flex items-center gap-2 mb-6 justify-center">
          <div class="w-24 h-px bg-gradient-to-r from-transparent via-blue-500 to-transparent"></div>
          <div class="w-2 h-2 bg-blue-500 rotate-45"></div>
          <div class="w-24 h-px bg-gradient-to-r from-transparent via-blue-500 to-transparent"></div>
        </div>

        <p class="text-xl text-slate-300 max-w-2xl mx-auto leading-relaxed">
          {{ t('journey.description') }}
        </p>
      </div>

      <div class="grid lg:grid-cols-2 gap-16">
        <!-- Left: Mission & Values -->
        <div>
          <!-- Mission -->
          <div class="flex items-center gap-4 mb-12">
            <div class="w-14 h-14 border-2 border-blue-500 bg-blue-500/10 flex items-center justify-center">
              <Compass class="w-7 h-7 text-blue-400" />
            </div>
            <h3 class="text-3xl text-white">{{ t('journey.missionTitle') }}</h3>
          </div>

          <div class="space-y-6 mb-16">
            <div
              v-for="key in missionKeys"
              :key="key"
              class="group border border-slate-800 bg-slate-900/30 backdrop-blur p-6 hover:border-blue-500/50 transition-all"
            >
              <div class="text-sm text-cyan-400 uppercase tracking-wider mb-3">
                {{ t(`journey.mission.${key}.label`) }}
              </div>
              <p class="text-slate-300 leading-relaxed">
                {{ t(`journey.mission.${key}.text`) }}
              </p>
            </div>
          </div>

          <!-- Values -->
          <div class="flex items-center gap-4 mb-8">
            <div class="w-14 h-14 border-2 border-violet-500 bg-violet-500/10 flex items-center justify-center">
              <Heart class="w-7 h-7 text-violet-400" />
            </div>
            <h3 class="text-3xl text-white">{{ t('journey.valuesTitle') }}</h3>
          </div>

          <div class="grid grid-cols-2 gap-4">
            <div
              v-for="key in valueKeys"
              :key="key"
              class="group border border-slate-800 bg-slate-900/30 backdrop-blur p-5 hover:border-violet-500/50 transition-all"
            >
              <h4 class="text-white mb-2 group-hover:text-violet-400 transition-colors">
                {{ t(`journey.values.${key}.name`) }}
              </h4>
              <p class="text-slate-400 text-sm leading-relaxed">
                {{ t(`journey.values.${key}.description`) }}
              </p>
            </div>
          </div>
        </div>

        <!-- Right: Team & Hiring -->
        <div>
          <!-- Team header -->
          <div class="flex items-center gap-4 mb-12">
            <div class="w-14 h-14 border-2 border-cyan-500 bg-cyan-500/10 flex items-center justify-center">
              <Users class="w-7 h-7 text-cyan-400" />
            </div>
            <h3 class="text-3xl text-white">{{ t('journey.teamTitle') }}</h3>
          </div>

          <!-- Founder -->
          <div class="border border-slate-800 bg-slate-900/30 backdrop-blur p-6 mb-8 hover:border-cyan-500/50 transition-all group">
            <div class="flex items-center gap-4 mb-4">
              <div class="w-16 h-16 border-2 border-cyan-500/50 bg-cyan-500/10 flex items-center justify-center group-hover:border-cyan-500 transition-all">
                <UserCircle class="w-8 h-8 text-cyan-400" />
              </div>
              <div>
                <div class="text-xs text-cyan-400 uppercase tracking-wider mb-1">Fondateur</div>
                <h4 class="text-xl text-white">{{ t('journey.founder.role') }}</h4>
              </div>
            </div>
            <p class="text-slate-300 text-sm leading-relaxed">
              {{ t('journey.founder.description') }}
            </p>
          </div>

          <!-- Network -->
          <div class="mb-8">
            <h4 class="text-lg text-slate-300 mb-4 flex items-center gap-2">
              <Network class="w-5 h-5 text-blue-400" />
              {{ t('journey.network.title') }}
            </h4>
            <div class="space-y-3">
              <div
                v-for="key in networkKeys"
                :key="key"
                class="group flex items-center gap-4 border border-slate-800 bg-slate-900/30 backdrop-blur p-4 hover:border-blue-500/50 transition-all"
              >
                <div class="w-10 h-10 border border-blue-500/30 bg-blue-500/10 flex items-center justify-center group-hover:bg-blue-500/20 transition-all">
                  <Sparkles class="w-5 h-5 text-blue-400" />
                </div>
                <div>
                  <div class="text-white text-sm">{{ t(`journey.network.roles.${key}.title`) }}</div>
                  <div class="text-slate-500 text-xs">{{ t(`journey.network.roles.${key}.description`) }}</div>
                </div>
              </div>
            </div>
          </div>

          <!-- Hiring CTA -->
          <div class="border-2 border-dashed border-green-500/30 bg-green-500/5 backdrop-blur p-6 hover:border-green-500/50 transition-all">
            <div class="flex items-center gap-3 mb-3">
              <div class="w-3 h-3 bg-green-400 rounded-full animate-pulse"></div>
              <span class="text-green-400 uppercase tracking-wider text-sm">{{ t('journey.hiring.badge') }}</span>
            </div>
            <h4 class="text-xl text-white mb-2">{{ t('journey.hiring.title') }}</h4>
            <p class="text-slate-300 text-sm leading-relaxed">
              {{ t('journey.hiring.description') }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
