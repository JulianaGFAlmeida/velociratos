<template>
  <div
    v-if="hasContent"
    :class="[
      'w-2xs h-[45vh] pt-6 text-center flex flex-col items-center',
      borderClass,
      bgClass,
      textClass
    ]"
  >
    <img
      :src="image"
      :alt="name"
      class="w-48 h-48 rounded-full object-cover mb-4"
    />
    <h2 class="text-[1.5rem] font-[Anton] leading-[20px]">{{ name }}</h2>
    <h3 class="text-[1.2rem] font-semibold mb-5 ">{{ role }}</h3>
    <div class="text-[1.1rem] max-w-[80%]">{{ description }}</div>

    <!-- Ícones clicáveis -->
    <div v-if="links?.length" class="flex gap-4 mt-4">
      <a
        v-for="(link, index) in links"
        :key="index"
        :href="link.url"
        target="_blank"
        rel="noopener noreferrer"
        class="hover:scale-110 transition-transform"
      >
        <img :src="link.icon" alt="" class="w-6 h-6" />
      </a>
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{
  image?: string
  name?: string
  role?: string
  description?: string
  borderClass?: string
  bgClass?: string
  textClass?: string
  links?: { icon: string; url: string }[]
}>()

// Computed simples para verificar se tem conteúdo mínimo para mostrar o card
const hasContent = Boolean(props.name && props.image)
</script>
