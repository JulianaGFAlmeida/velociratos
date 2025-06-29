<template>
  <h1 class="font-[Anton] px-10 text-4xl mt-8 mb-6">O CARRINHO</h1>

  <!-- Imagem grande -->
  <div class="w-full h-auto">
    <img
      :src="selectedImage"
      alt="Imagem grande selecionada"
      class="w-full h-auto object-cover rounded"
    />
  </div>

  <!-- Galeria de imagens pequenas -->
  <div class="flex justify-center items-center gap-4 mt-5 overflow-x-auto px-4 py-2">
    <div
      v-for="(img, index) in images"
      :key="index"
      class="w-20 h-20 rounded cursor-pointer overflow-hidden"
      @click="selectImage(img)"
    >
      <img
        :src="img"
        alt="Imagem pequena"
        class="w-full h-full object-cover rounded transition-opacity duration-200"
        :class="selectedImage === img ? 'opacity-100' : 'opacity-40'"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// Importa imagens via ESModules (requer para funcionar no Netlify)
import carrinho1 from '../assets/imgs/carrinho/montagem_carrinho.jpg'
import carrinho2 from '../assets/imgs/carrinho/montagem_carrinho2.jpg'
import carrinho3 from '../assets/imgs/carrinho/Preparacao_carrinho.jpg'
import carrinho4 from '../assets/imgs/carrinho/Preparacao_carrinho2.jpg'
// Adicione mais imagens se necessário

const images = [
  carrinho4,
  carrinho3,
  carrinho2,
  carrinho1,
]

const selectedImage = ref(images[0])

function selectImage(img: string) {
  selectedImage.value = img
}
</script>
