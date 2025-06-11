<template>
  <section class="w-full">
    <h1 class="font-[Anton] px-10 text-4xl mt-8 mb-6">NOSSA EQUIPE</h1>

    <div class="px-10 relative">
      <Splide
        :options="splideOptions"
        aria-label="Carousel da equipe"
      >
        <SplideSlide v-for="(member, index) in members" :key="index">
          <MemberCard
            :image="member.image"
            :name="member.name"
            :role="member.role"
            :description="member.description"
            :borderClass="member.borderClass"
            :bgClass="member.bgClass"
            :textClass="member.textClass"
            :links="member.links"
          />
        </SplideSlide>
      </Splide>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { Splide, SplideSlide } from '@splidejs/vue-splide'
import MemberCard from '../components/MemberCard.vue'
import joaoPedro from '../assets/imgs/equipe/joao_pedro_pansardi.jpg';
import aliceCosta from '../assets/imgs/equipe/Alice_Costa_de_Lima.jpg';
import andreMiyaki from '../assets/imgs/equipe/andre_miyake.jpg'; 
import andreSampaio from '../assets/imgs/equipe/andre_sampaio.jpg'; 
import julianaAlmeida from '../assets/imgs/equipe/juliana_almeida.jpg'; 
import kauanTurini from '../assets/imgs/equipe/kauan_turini.jpg'; 
import pedroHenrique from '../assets/imgs/equipe/pedro_henrique.jpg'; 
import linkedin from '../assets/icons/linkedin.png';
import email from '../assets/icons/email.png';
import instagram from '../assets/icons/instagram.png';

const splideOptions = {
  type: 'slide',
  perPage: 5,       // número de cards visíveis por slide
  perMove: 5,       // avança a página inteira
  gap: '1rem',
  pagination: false, // bolinhas por página
  arrows: true,
  rewind: false,
  breakpoints: {
    1024: { perPage: 3, perMove: 3 },
    768: { perPage: 2, perMove: 2 },
    640: { perPage: 1, perMove: 1 },
  },
}


const members = ref([
  {
    image: aliceCosta,
    name: 'Alice Costa de Lima',
    role: 'Marketing',
    description: 'Coordenadora das equipes marketing e escrita/texto',
    borderClass: 'border-1 border-white',
    bgClass: '',
    textClass: 'text-white',
    links: [{ icon: email, url: 'mailto:alicecostalima@alunos.utfpr.edu.br' }, { icon: linkedin, url: 'https://www.linkedin.com/in/alice-costa-de-lima-473b61250/' }]
  },
  {
    image: andreMiyaki,
    name: 'André Miyake',
    role: 'Líder',
    description: 'Gestor da equipe Velociratos',
    borderClass: 'border-1 border-white',
    bgClass: '',
    textClass: 'text-white',
    links: [{ icon: email, url: 'mailto:andreryuhei@gmail.com' },{ icon: instagram, url: 'https://www.instagram.com/andreryuhei/' }]
  },
  {
    image: andreSampaio,
    name: 'André Sampaio',
    role: 'Vice Líder',
    description: 'Coordenador da equipe de Design e Mecânica',
    borderClass: 'border-1 border-white',
    bgClass: '',
    textClass: 'text-white',
    links: [{ icon: email, url: 'mailto:andreleonardosampaio@alunos.utfpr.edu.br' },{ icon: linkedin, url: 'https://linkedin.com/comm/mynetwork/discovery-see-all?usecase=PEOPLE_FOLLOWS&followMember=andré-sampaio-47793436a' }]
  },
  {
    image: joaoPedro,
    name: 'João Pedro Pansardi',
    role: 'Marketing',
    description: 'Responsável pelo nome e logo do carro',
    borderClass: 'border-1 border-white',
    bgClass: '',
    textClass: 'text-white',
  },
  {
    image: julianaAlmeida,
    name: 'Juliana Almeida',
    role: 'Design/Mecânica',
    description: 'TI e auxílio na montagem do carro e design',
    borderClass: 'border-1 border-white',
    bgClass: '',
    textClass: 'text-white',
    links: [{ icon: email, url: 'mailto:julianaguimafeijo@gmail.com' },{ icon: linkedin, url: 'https://linkedin.com/in/juliana-almeida-688758165/' }]
  },
  {
    image: kauanTurini,
    name: 'Kauan Turini',
    role: 'Design/Mecânica',
    description: 'Auxilio na montagem do carro e design',
    borderClass: 'border-1 border-white',
    bgClass: '',
    textClass: 'text-white'
  },
  {
    image: pedroHenrique,
    name: 'Pedro Henrique',
    role: 'Marketing/Mecânica',
    description: 'Responsável pela logo e montagem do carro',
    borderClass: 'border-1 border-white',
    bgClass: '',
    textClass: 'text-white',
    links: [{ icon: instagram, url: 'https://www.instagram.com/p.zambon_/' }]
  }
  // adicione outros membros aqui
])
</script>