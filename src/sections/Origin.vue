<template>
  <!-- MOBILE layout -->
  <div class="flex flex-col items-center justify-center text-center md:hidden">
    <!-- Texto -->
    <div class="p-5 text-[1.5em] text-justify max-w-prose leading-10">
      <p>Velociratos nasceu da fusão entre velocidade e engenhosidade.</p>
      <p>
        Unimos o velociraptor, símbolo de força e agilidade com o rato, que representa
        a ratoeira usada no projeto e a inteligência por trás da nossa criação.
      </p>
      <br />
      <p>O nome traduz o espírito da nossa equipe: veloz e criativa</p>
    </div>

    <!-- Imagens lado a lado -->
    <div class="flex flex-row items-center justify-center gap-5 p-5">
      <img src="../assets/imgs/marca/dinossauro_velociratos.png" alt="dinossauro da logo" class="w-[40vw] h-auto" />
      <img src="../assets/imgs/marca/rato_velociratos.png" alt="rato da logo" class="w-[40vw] h-auto" />
    </div>
  </div>

  <!-- DESKTOP layout -->
  <div class="hidden md:flex flex-row items-center justify-center text-left">
    <!-- Imagem esquerda -->
    <div class="p-5">
      <img src="../assets/imgs/marca/dinossauro_velociratos.png" alt="dinossauro da logo" class="w-[25vw] h-auto" />
    </div>

    <!-- Texto -->
    <div class="p-5 text-[1.5em] text-justify max-w-prose">
      <p>Velociratos nasceu da fusão entre velocidade e engenhosidade.</p>
      <p>
        Unimos o velociraptor, símbolo de força e agilidade com o rato, que representa
        a ratoeira usada no projeto e a inteligência por trás da nossa criação.
      </p>
      <br />
      <p>O nome traduz o espírito da nossa equipe: veloz e criativa</p>
    </div>

    <!-- Imagem direita -->
    <div class="p-5">
      <img src="../assets/imgs/marca/rato_velociratos.png" alt="rato da logo" class="w-[25vw] h-auto" />
    </div>
  </div>
</template>

<script setup lang="ts">
</script>
