<template>
  <div class="news-section">
    <div class="row">
      <div class="col" v-for="(item, index) in newsItems.slice(0, 3)" :key="index">
        <div class="news-item">
          <img :src="item.imageUrl" alt="News Image" class="news-image">
          <div class="news-title">{{ item.title }}</div>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col" v-for="(item, index) in newsItems.slice(3, 6)" :key="index">
        <div class="news-item">
          <img :src="item.imageUrl" alt="News Image" class="news-image">
          <div class="news-title">{{ item.title }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import img_1 from '../assets/img-1.png';
import img_2 from '../assets/img-2.png';
import img_3 from '../assets/img-3.png';
import img_4 from '../assets/img-4.png';
import img_5 from '../assets/img-5.png';
import img_6 from '../assets/img-6.png';

export default {
  name: 'NewsSection',
  data() {
    return {
      newsItems: [
        { title: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.', imageUrl: img_1 },
        { title: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.', imageUrl: img_2 },
        { title: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.', imageUrl: img_3 },
        { title: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.', imageUrl: img_4 },
        { title: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.', imageUrl: img_5 },
        { title: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.', imageUrl: img_6 }
      ]
    };
  }
};
</script>

<style scoped>
.news-section {
  margin-top: 20px;
  padding: 20px; /* Ajuste do preenchimento para ser mais flexível */
}

.row {
  display: flex;
  justify-content: center; /* Centraliza o conteúdo horizontalmente */
  margin-bottom: 20px;
  gap: 20px; /* Adiciona um espaçamento entre as colunas */
  flex-wrap: wrap; /* Permite que as colunas se ajustem em várias linhas */
}

.col {
  flex: 0 0 calc(33.33% - 20px);
  max-width: calc(33.33% - 20px);
}

.news-item {
  position: relative;
  text-align: center;
  margin-bottom: 20px;
}

.news-image {
  width: 100%;
  max-width: 100%;
  height: auto;
}

.news-title {
  position: absolute;
  bottom: 10px;
  left: 0;
  width: 100%;
  background: rgba(0, 0, 0, 0.6);
  color: white;
  padding: 10px;
  font-size: 16px;
  font-weight: bold;
}

/* Media queries para responsividade */
@media (max-width: 992px) {
  .col {
    flex: 0 0 calc(50% - 20px);
    max-width: calc(50% - 20px);
  }
}

@media (max-width: 576px) {
  .col {
    flex: 0 0 100%;
    max-width: 100%;
  }
}
</style>
