<template>
  <div class="carousel-container">
    <img src="../assets/thumb dia 18-1.jpg" alt="">
    <div class="header-overlay">
      <h2 class="section-title">Episódios Recentes</h2>
      <p class="section-description">Confira os últimos episódios do nosso canal</p>
    </div>
    <div class="youtube-carousel">
      <carousel
        :per-page="perPage"
        :navigation-enabled="true"
        
      >
        <slide v-for="(video, index) in videos" :key="index">
          <div class="video-container">
            <iframe
              :src="`https://www.youtube.com/embed/${video.id}`"
              style="border: none"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
              allowfullscreen
            >
            </iframe>
          </div>
        </slide>
      </carousel>
    </div>
  </div>
</template>

<script>
import { Carousel, Slide } from "vue-carousel";

export default {
  name: "YouTubeCarousel",
  components: {
    Carousel,
    Slide,
  },
  data() {
    return {
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
  },
};
</script>

<style scoped>
.carousel-container {
  width: 100%;
  margin: 0 auto;
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

.section-title {
  font-size: 24px;
  margin: 0;
}

.section-description {
  font-size: 16px;
  margin: 0;
}

.VueCarousel-dot{
  color: #ffffff;
  background-color: #ffffff;
}

.youtube-carousel {
  width: 80%;
  margin: 0 auto;
  position: relative;
  z-index: 1;
}



.carousel__next{
  color: #ffffff;
  background-color: #ffffff;
}

.VueCarousel-navigation-prev {
 right: -50px;;
}

.VueCarousel-navigation-next {
 
  color: #ffffff;
  background-color: #ffffff;
}



.VueCarousel-navigation-button:hover,
.VueCarousel-navigation-button:focus {
  outline: none;
}

.video-container {
  position: relative;
  padding-bottom: 56.25%;
  height: 0;
  margin: 10px 0 10px 0;
}

.VueCarousel-slide{
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
    width: 90%;
  }
}

@media (max-width: 576px) {
  .youtube-carousel {
    width: 100%;
  }
}
</style>
