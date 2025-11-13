<script setup lang="ts">
import { ref } from 'vue'
import { Mail, Phone, MapPin, Send, MessageSquare, Linkedin } from 'lucide-vue-next'

const formData = ref({
  email: '',
  message: ''
})

const handleSubmit = (e: Event) => {
  e.preventDefault()
  // Handle form submission
  console.log('Form submitted:', formData.value)
}

const contactMethods = [
  {
    icon: Mail,
    label: 'Email',
    value: 'johary@example.com',
    link: 'mailto:johary@example.com',
    color: 'blue'
  },
  {
    icon: Phone,
    label: 'Téléphone',
    value: '+261 34 00 000 00',
    link: 'tel:+261340000000',
    color: 'cyan'
  },
  {
    icon: MapPin,
    label: 'Localisation',
    value: 'Madagascar',
    link: '#',
    color: 'violet'
  }
]

const socialLinks = [
  {
    icon: MessageSquare,
    label: 'Messenger',
    username: '@johary.fiononana',
    link: '#',
    color: 'blue'
  },
  {
    icon: MessageSquare,
    label: 'WhatsApp',
    username: '+261 34 00 000 00',
    link: '#',
    color: 'green'
  },
  {
    icon: Linkedin,
    label: 'LinkedIn',
    username: 'Johary Fiononana',
    link: '#',
    color: 'cyan'
  }
]
</script>

<template>
  <div class="min-h-screen px-8 md:px-16 lg:px-24 py-32">
    <div class="max-w-7xl mx-auto">
      <!-- Header -->
      <div class="mb-20 text-center relative">
        <div class="inline-flex items-center gap-3 border border-blue-500/30 bg-blue-500/10 backdrop-blur px-4 py-2 mb-6">
          <div class="w-2 h-2 bg-blue-400 rotate-45"></div>
          <span class="text-sm text-blue-400 tracking-[0.3em] uppercase">Restons connectés</span>
        </div>
        
        <h2 class="text-6xl lg:text-7xl tracking-tight mb-6">
          <span class="bg-gradient-to-r from-white via-blue-100 to-white bg-clip-text text-transparent">
            Contactez-moi
          </span>
        </h2>
        
        <div class="flex items-center gap-2 mb-6 justify-center">
          <div class="w-24 h-px bg-gradient-to-r from-transparent via-blue-500 to-transparent"></div>
          <div class="w-2 h-2 bg-blue-500 rotate-45"></div>
          <div class="w-24 h-px bg-gradient-to-r from-transparent via-blue-500 to-transparent"></div>
        </div>

        <p class="text-xl text-slate-300 max-w-2xl mx-auto leading-relaxed">
          Une question, un projet ? N'hésitez pas à me contacter. 
          Je serai ravi d'échanger avec vous.
        </p>
      </div>

      <div class="grid lg:grid-cols-2 gap-16">
        <!-- Contact Form -->
        <div class="order-2 lg:order-1">
          <form @submit="handleSubmit" class="space-y-6">
            <!-- Email Input -->
            <div class="group">
              <label class="block text-sm text-slate-300 uppercase tracking-wider mb-2">
                Email
              </label>
              <div class="relative">
                <input
                  v-model="formData.email"
                  type="email"
                  required
                  placeholder="votre.email@example.com"
                  class="w-full px-4 py-4 border-2 border-slate-600 bg-slate-900/50 text-white placeholder-slate-400 focus:border-blue-500 focus:outline-none transition-all"
                />
                <div class="absolute bottom-0 left-0 right-0 h-px bg-gradient-to-r from-blue-500 to-transparent scale-x-0 group-focus-within:scale-x-100 transition-transform"></div>
              </div>
            </div>

            <!-- Message Textarea -->
            <div class="group">
              <label class="block text-sm text-slate-500 uppercase tracking-wider mb-2">
                Message
              </label>
              <div class="relative">
                <textarea
                  v-model="formData.message"
                  required
                  rows="6"
                  placeholder="Décrivez votre projet..."
                  class="w-full px-4 py-4 border-2 border-slate-600 bg-slate-900/50 text-white placeholder-slate-400 focus:border-blue-500 focus:outline-none transition-all resize-none"
                ></textarea>
                <div class="absolute bottom-0 left-0 right-0 h-px bg-gradient-to-r from-blue-500 to-transparent scale-x-0 group-focus-within:scale-x-100 transition-transform"></div>
              </div>
            </div>

            <!-- Submit Button -->
            <button
              type="submit"
              class="group/btn relative w-full px-8 py-4 border-2 border-blue-500 bg-blue-500 text-white overflow-hidden hover:border-blue-400 transition-all"
            >
              <span class="relative z-10 flex items-center justify-center gap-2 tracking-wider uppercase text-sm">
                Envoyer le message
                <Send class="w-4 h-4 group-hover/btn:translate-x-1 group-hover/btn:-translate-y-1 transition-transform" />
              </span>
              <div class="absolute inset-0 bg-gradient-to-r from-blue-600 to-violet-600 opacity-0 group-hover/btn:opacity-100 transition-opacity"></div>
            </button>
          </form>

          <!-- Additional Note -->
          <div class="mt-8 border border-slate-800 bg-slate-900/30 backdrop-blur p-6">
            <div class="flex items-start gap-3">
              <div class="w-2 h-2 bg-green-400 rounded-full mt-2 animate-pulse"></div>
              <p class="text-slate-300 text-sm leading-relaxed">
                💡 N'hésitez pas à me contacter—je suis là 
                pour vous aider ! Que ce soit sur le formulaire ci-dessus, sur WhatsApp et Messenger 💬, ou directement 
                par e-mail 📧, je serai toujours ravi d'échanger, discuter de votre vision, et travailler ensemble pour 
                concrétiser vos projets 🚀
              </p>
            </div>
          </div>
        </div>

        <!-- Contact Info -->
        <div class="order-1 lg:order-2 space-y-8">
          <div>
            <h3 class="text-3xl text-white mb-8">Mes coordonnées</h3>
            
            <div class="space-y-4 mb-12">
              <a
                v-for="(method, index) in contactMethods"
                :key="index"
                :href="method.link"
                class="group flex items-center gap-4 border border-slate-800 bg-slate-900/30 backdrop-blur p-4 hover:border-blue-500/50 transition-all"
              >
                <div :class="`w-12 h-12 border border-${method.color}-500/30 bg-${method.color}-500/10 flex items-center justify-center group-hover:bg-${method.color}-500/20 transition-all`">
                  <component :is="method.icon" :class="`w-5 h-5 text-${method.color}-400`" />
                </div>
                <div class="flex-1">
                  <div class="text-xs text-slate-300 uppercase tracking-wider mb-1">{{ method.label }}</div>
                  <div class="text-white group-hover:text-blue-400 transition-colors">{{ method.value }}</div>
                </div>
                <div class="w-8 h-8 border border-slate-800 flex items-center justify-center group-hover:border-blue-500 transition-all">
                  <div class="w-1 h-1 bg-slate-500 group-hover:bg-blue-400 transition-colors"></div>
                </div>
              </a>
            </div>
          </div>

          <!-- Social Links -->
          <div class="border border-slate-800 bg-slate-900/30 backdrop-blur p-8">
            <div class="flex items-center gap-2 mb-6">
              <div class="w-2 h-2 bg-green-400 rounded-full animate-pulse"></div>
              <p class="text-slate-300">
                Explorez mes profils sociaux et restons connectés !
              </p>
            </div>

            <div class="space-y-4">
              <a
                v-for="(social, index) in socialLinks"
                :key="index"
                :href="social.link"
                class="group flex items-center justify-between border border-slate-800 bg-slate-900/30 p-4 hover:border-blue-500/50 transition-all"
              >
                <div class="flex items-center gap-3">
                  <div :class="`w-10 h-10 border border-${social.color}-500/30 bg-${social.color}-500/10 flex items-center justify-center group-hover:bg-${social.color}-500/20 transition-all`">
                    <component :is="social.icon" :class="`w-5 h-5 text-${social.color}-400`" />
                  </div>
                  <div>
                    <div class="text-xs text-slate-300 uppercase tracking-wider">{{ social.label }}</div>
                    <div class="text-white group-hover:text-blue-400 transition-colors">{{ social.username }}</div>
                  </div>
                </div>
                <div class="w-6 h-6 border border-slate-800 flex items-center justify-center group-hover:border-blue-500 transition-all">
                  <div class="w-1 h-1 bg-slate-500 group-hover:bg-blue-400 transition-colors"></div>
                </div>
              </a>
            </div>
          </div>

          <!-- Availability Badge -->
          <div class="border-2 border-green-500/30 bg-green-500/10 backdrop-blur p-6">
            <div class="flex items-center gap-3 mb-3">
              <div class="w-3 h-3 bg-green-400 rounded-full animate-pulse"></div>
              <span class="text-green-400 uppercase tracking-wider text-sm">Disponible pour nouveaux projets</span>
            </div>
            <p class="text-slate-300 text-sm">
              Actuellement ouvert aux opportunités freelance et collaborations.
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
