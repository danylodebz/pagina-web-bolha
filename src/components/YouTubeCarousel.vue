<template>
  <div class="carousel-container">
    <div class="separator"></div> <!-- Linha de separação -->
    <div class="header-overlay">
      <h2 class="section-title">Episódios</h2>
      <p class="section-description">Confira todos os episódios da primeira temporada</p>
    </div>
    
    <div class="youtube-carousel">
      <carousel
        ref="carousel"
        :per-page="perPage"
        :navigationEnabled="false"
        :paginationEnabled="false"
        :loop="false"
        :scrollPerPage="true"
      >
        <slide v-for="(video, index) in videos" :key="index">
          <div class="video-container">
            <iframe
              :src="`https://www.youtube.com/embed/${video.id}`"
              style="border: none"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
              allowfullscreen
            ></iframe>
          </div>
        </slide>
      </carousel>
      <div class="navigation">
        <button class="carousel-prev" @click="prevSlide">
          <img :src="prevButtonImage" alt="Anterior">
        </button>
        <button class="carousel-next" @click="nextSlide">
          <img :src="nextButtonImage" alt="Próximo">
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { Carousel, Slide } from 'vue-carousel';
import headerImage from '../assets/bolha2.jpeg';
import prevButtonImage from '@/assets/seta-esquerda.png';
import nextButtonImage from '@/assets/seta-direita.png';

export default {
  name: 'YouTubeCarousel',
  components: {
    Carousel,
    Slide,
  },
  data() {
    return {
      headerImage: headerImage,
      videos: [
        { id: "Vu7KrhblBYg" },
        { id: "RmZ5VznWgAg" },
        { id: "qmkJq-3_1Gw" },
        { id: "z7DfJQb7RFI" },
        { id: "urLSYpC814M" },
        { id: "y10rZt74UMc" },
        { id: "urLSYpC814M" },
        { id: "cCjeJyx6sWk" },
        { id: "aWXTlj21C0o" },
        { id: "8jlkY6KOofE" },
        { id: "4GN6VmDQn0k" },
        { id: "MbjZkLJrrAs" },
        { id: "xDehGpn1FT0" },
        { id: "qkGgTGtG6q0" },
        { id: "3wDcYGU1QL0" },
        { id: "oa03llJgt-Y" },
        { id: "qtJqO6ga0SY" },
        { id: "8YQHaCvEaDY" },
        { id: "GlwP-Fr1k3U" },
        { id: "bsMAOOQuJy4" },
        { id: "D5SSeUJeRIs" },
        { id: "KuDwjWE-W3Y" },
        { id: "PUpPTPsqQt8" },
        { id: "3wDcYGU1QL0" },
      ],
      perPage: 3, // Default value for larger screens
      prevButtonImage: prevButtonImage,
      nextButtonImage: nextButtonImage
    };
  },
  created() {
    // Adjust perPage based on the screen size
    this.updatePerPage();
    window.addEventListener('resize', this.updatePerPage);
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.updatePerPage);
  },
  methods: {
    updatePerPage() {
      const width = window.innerWidth;
      if (width <= 576) {
        this.perPage = 1;
      } else if (width <= 992) {
        this.perPage = 2;
      } else {
        this.perPage = 3;
      }
    },
    prevSlide() {
      console.log("Slide anterior");
      if (this.$refs.carousel) {
        this.$refs.carousel.goToPage(this.$refs.carousel.currentPage - 1);
      }
    },
    nextSlide() {
      console.log("Next slide");
      if (this.$refs.carousel) {
        this.$refs.carousel.goToPage(this.$refs.carousel.currentPage + 1);
      }
    }
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

.carousel-container {
  width: 100%;
  margin: 0 auto;
  font-family: 'Inter', sans-serif; /* Aplica a fonte Inter */
}

img {
  width: 100%;
}

.header-overlay {
  text-align: center;
  background: rgba(0, 0, 0, 0.5);
  color: #ffffff;
  padding: 10px 20px;
  border-radius: 10px;
  margin-top: 50px; /* Adjust the top margin as needed */
  margin-bottom: 20px; /* Adjust the bottom margin as needed */
}

.separator {
  width: 100%;
  height: 7px;
  background-color: #585858;
  margin: 20px 0; /* Margem para criar espaçamento */
}

.section-title {
  font-size: 24px;
  margin: 0;
}

.section-description {
  font-size: 16px;
  margin: 0;
}

.VueCarousel-dot {
  display: none; /* Esconde os pontinhos de navegação */
}

.youtube-carousel {
  width: 100%; /* Alterado para 100% */
  margin: 0 auto;
  position: relative;
  z-index: 1;
}

.navigation {
  position: absolute;
  top: 50%;
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: space-between;
  transform: translateY(-50%);
  z-index: 2; /* Garante que os botões estejam acima dos vídeos */
}

.carousel-prev,
.carousel-next {
  background: rgba(0, 0, 0, 0.5); /* Fundo transparente escuro */
  border: none;
  cursor: pointer;
}

.carousel-prev:hover,
.carousel-next:hover {
  background: rgba(0, 0, 0, 0.7); /* Fundo mais escuro ao passar o mouse */
}

.carousel-prev {
  left: 0; /* Ajustado para alinhar ao vídeo da extremidade esquerda */
}

.carousel-next {
  right: 0; /* Ajustado para alinhar ao vídeo da extremidade direita */
}

.carousel-prev img,
.carousel-next img {
  width: 50px;
  height: 50px;
}

.video-container {
  position: relative;
  padding-bottom: 56.25%;
  height: 0;
  margin: 10px 0 10px 0;
}

.VueCarousel-slide {
  margin-right: 10px;
}

.video-container iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: none;
}

/* Media queries para responsividade */
@media (max-width: 992px) {
  .youtube-carousel {
    width: 100%; /* Certifique-se de que seja 100% em todos os tamanhos de tela */
  }

  .carousel-prev img,
  .carousel-next img {
    width: 40px;
    height: 40px;
  }
}

@media (max-width: 576px) {
  .youtube-carousel {
    width: 100%; /* Certifique-se de que seja 100% em todos os tamanhos de tela */
  }

  .carousel-prev img,
  .carousel-next img {
    width: 30px;
    height: 30px;
  }
}
</style>
