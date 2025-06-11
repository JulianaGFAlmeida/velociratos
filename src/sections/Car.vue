<template>
  <h1 class="font-[Anton] px-10 text-4xl mt-8 mb-6">O CARRINHO</h1>

  <div class="w-full h-auto">
    <img
      :src="selectedImage"
      alt="Imagem grande selecionada"
      class="w-full h-auto object-cover rounded"
    />
  </div>

  <div class="flex justify-center items-center gap-4 mt-5 overflow-x-auto px-4 py-2">
    <div
      v-for="(img, index) in images"
      :key="index"
      class="relative w-20 h-20 rounded cursor-pointer border-4 border-transparent overflow-hidden"
      @click="selectImage(img)"
    >
      <img
        :src="img"
        alt="Imagem pequena"
        class="w-full h-full object-cover rounded"
      />

      <!-- Overlay Tailwind (agora deve funcionar com o arquivo de config!) -->
      <div
        v-if="selectedImage !== img"
        class="absolute inset-0 bg-black bg-opacity-40 pointer-events-none rounded"
      ></div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

import placeholder from '../assets/imgs/carrinho/placeholder.jpg'
import placeholder1 from '../assets/imgs/carrinho/placeholder1.jpg'
import placeholder2 from '../assets/imgs/carrinho/placeholder2.jpg'

const images = [
  placeholder,
  placeholder1,
  placeholder2,
]

const selectedImage = ref(images[0])

function selectImage(img: string) {
  selectedImage.value = img
}
</script>
