<script setup lang="ts">
import { ref, onMounted, onUnmounted, watch } from 'vue'

interface Props {
  activeSection: string
}

const props = defineProps<Props>()

const canvasRef = ref<HTMLCanvasElement | null>(null)

// Define color schemes for each section
const colorSchemes: Record<string, { primary: string; secondary: string; accent: string }> = {
  home: { primary: '59, 130, 246', secondary: '139, 92, 246', accent: '6, 182, 212' },
  services: { primary: '139, 92, 246', secondary: '168, 85, 247', accent: '236, 72, 153' },
  skills: { primary: '6, 182, 212', secondary: '59, 130, 246', accent: '139, 92, 246' },
  journey: { primary: '99, 102, 241', secondary: '139, 92, 246', accent: '59, 130, 246' },
  contact: { primary: '34, 211, 238', secondary: '6, 182, 212', accent: '59, 130, 246' }
}

const getColors = () => colorSchemes[props.activeSection] || colorSchemes.home

// Particle system
class Particle {
  x: number
  y: number
  vx: number
  vy: number
  size: number
  opacity: number
  colorIndex: number
  canvas: HTMLCanvasElement

  constructor(canvas: HTMLCanvasElement) {
    this.canvas = canvas
    this.x = Math.random() * canvas.width
    this.y = Math.random() * canvas.height
    this.vx = (Math.random() - 0.5) * 0.5
    this.vy = (Math.random() - 0.5) * 0.5
    this.size = Math.random() * 2 + 1
    this.opacity = Math.random() * 0.5 + 0.2
    this.colorIndex = Math.floor(Math.random() * 3)
  }

  update() {
    this.x += this.vx
    this.y += this.vy

    // Wrap around edges
    if (this.x < 0) this.x = this.canvas.width
    if (this.x > this.canvas.width) this.x = 0
    if (this.y < 0) this.y = this.canvas.height
    if (this.y > this.canvas.height) this.y = 0
  }

  draw(ctx: CanvasRenderingContext2D, colors: { primary: string; secondary: string; accent: string }) {
    ctx.beginPath()
    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2)
    
    const colorValues = [colors.primary, colors.secondary, colors.accent]
    ctx.fillStyle = `rgba(${colorValues[this.colorIndex]}, ${this.opacity})`
    ctx.fill()
  }
}

let animationFrameId: number | null = null
let particles: Particle[] = []

const initCanvas = () => {
  const canvas = canvasRef.value
  if (!canvas) return

  const ctx = canvas.getContext('2d')
  if (!ctx) return

  // Set canvas size
  const resizeCanvas = () => {
    canvas.width = window.innerWidth
    canvas.height = window.innerHeight
  }
  resizeCanvas()
  window.addEventListener('resize', resizeCanvas)

  // Create particles
  particles = []
  const particleCount = 100
  for (let i = 0; i < particleCount; i++) {
    particles.push(new Particle(canvas))
  }

  // Animation loop
  const animate = () => {
    const colors = getColors()
    ctx.fillStyle = 'rgba(2, 6, 23, 0.1)'
    ctx.fillRect(0, 0, canvas.width, canvas.height)

    particles.forEach(particle => {
      particle.update()
      particle.draw(ctx, colors)
    })

    // Draw connections
    particles.forEach((particle, i) => {
      for (let j = i + 1; j < particles.length; j++) {
        const dx = particle.x - particles[j].x
        const dy = particle.y - particles[j].y
        const distance = Math.sqrt(dx * dx + dy * dy)

        if (distance < 150) {
          ctx.beginPath()
          ctx.strokeStyle = `rgba(${colors.primary}, ${0.2 * (1 - distance / 150)})`
          ctx.lineWidth = 0.5
          ctx.moveTo(particle.x, particle.y)
          ctx.lineTo(particles[j].x, particles[j].y)
          ctx.stroke()
        }
      }
    })

    animationFrameId = requestAnimationFrame(animate)
  }

  animate()

  return () => {
    window.removeEventListener('resize', resizeCanvas)
    if (animationFrameId) {
      cancelAnimationFrame(animationFrameId)
    }
  }
}

onMounted(() => {
  const cleanup = initCanvas()
  
  onUnmounted(() => {
    if (cleanup) cleanup()
    if (animationFrameId) {
      cancelAnimationFrame(animationFrameId)
    }
  })
})

// Watch for section changes to update colors
watch(() => props.activeSection, () => {
  // Colors will automatically update on next animation frame
})
</script>

<template>
  <canvas 
    ref="canvasRef" 
    class="fixed inset-0 pointer-events-none z-0"
  ></canvas>
</template>
