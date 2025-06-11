<template>
  <div class="carousel-container" ref="container">
    <button class="nav prev" @click="prev" :disabled="currentSlide === 0">‹</button>
    
    <div class="carousel-wrapper" :style="{ overflow: 'hidden' }">
      <div
        class="carousel-track"
        :style="{
          display: 'flex',
          transition: 'transform 0.3s ease',
          transform: `translateX(-${currentSlide * slideWidth}px)`,
          width: trackWidth + 'px'
        }"
      >
        <!-- Renderiza os cards do slide atual -->
        <slot v-for="index in visibleIndices" :index="index" :key="index" />
      </div>
    </div>
    
    <button class="nav next" @click="next" :disabled="currentSlide >= maxSlide">›</button>

    <div class="dots">
      <button
        v-for="(dot, i) in totalSlides"
        :key="i"
        @click="goToSlide(i)"
        :class="{ active: currentSlide === i }"
        class="dot"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted, watch } from 'vue'

const props = defineProps<{
  slideCount: number
  cardWidth: number
}>()

const container = ref<HTMLElement | null>(null)
const currentSlide = ref(0)
const containerWidth = ref(0)

// Calcula quantos cards cabem inteiros na largura do container
const cardsPerSlide = computed(() => {
  if (!containerWidth.value) return 1
  return Math.max(1, Math.floor(containerWidth.value / props.cardWidth))
})

// Total de slides (dividindo o total de cards pelo que cabe por slide)
const totalSlides = computed(() =>
  Math.ceil(props.slideCount / cardsPerSlide.value)
)

// largura do slide (cardsPerSlide * largura do card)
const slideWidth = computed(() => cardsPerSlide.value * props.cardWidth)

// largura total do track
const trackWidth = computed(() => props.slideCount * props.cardWidth)

const maxSlide = computed(() => totalSlides.value - 1)

// Os índices absolutos dos membros que aparecem no slide atual
const visibleIndices = computed(() => {
  const start = currentSlide.value * cardsPerSlide.value
  const end = start + cardsPerSlide.value
  const indices = []
  for (let i = start; i < end && i < props.slideCount; i++) {
    indices.push(i)
  }
  return indices
})

function next() {
  if (currentSlide.value < maxSlide.value) {
    currentSlide.value++
  }
}

function prev() {
  if (currentSlide.value > 0) {
    currentSlide.value--
  }
}

function goToSlide(index: number) {
  currentSlide.value = index
}

onMounted(() => {
  if (container.value) {
    containerWidth.value = container.value.clientWidth
  }
})

window.addEventListener('resize', () => {
  if (container.value) {
    containerWidth.value = container.value.clientWidth
  }
})
</script>

<style scoped>
.carousel-container {
  position: relative;
  width: 100%;
  user-select: none;
}

.carousel-wrapper {
  overflow: hidden;
}

.carousel-track {
  display: flex;
  will-change: transform;
}

.nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: #333;
  border: none;
  color: white;
  font-size: 2rem;
  cursor: pointer;
  padding: 0 0.5rem;
  z-index: 10;
  opacity: 0.7;
  transition: opacity 0.3s;
}

.nav:disabled {
  opacity: 0.3;
  cursor: default;
}

.nav.prev {
  left: 0;
}

.nav.next {
  right: 0;
}

.dots {
  text-align: center;
  margin-top: 1rem;
}

.dot {
  border: none;
  background: #ccc;
  width: 12px;
  height: 12px;
  margin: 0 4px;
  border-radius: 50%;
  cursor: pointer;
}

.dot.active {
  background: #333;
}
</style>
