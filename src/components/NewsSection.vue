<template>
  <div class="news-section">
    <h2 class="section-title">Últimas Notícias</h2>
    <div class="divider"></div>
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
import img_1 from '../assets/tema_bolha.jpg';
import img_2 from '../assets/final.jpeg';
import img_3 from '../assets/victor_hugo.jpeg';
import img_4 from '../assets/meteoumatch.png';
import img_5 from '../assets/memes.png';
import img_6 from '../assets/fefi.jpg';

export default {
  name: 'NewsSection',
  data() {
    return {
      newsItems: [
        { title: 'Inscrições abertas para segunda temporada de A bolha.', imageUrl: img_1 },
        { title: 'Final formada! Vote em quem você escolhe para vencer a primeira temporada de A bolha', imageUrl: img_2 },
        { title: 'Após sucesso do reality A bolha, victor hugo cria novo reality de relacionamento entitulado mete ou match', imageUrl: img_3 },
        { title: 'Inscrições abertas para a primeira temporada de mete ou match. Clique para se inscrever', imageUrl: img_4 },
        { title: 'Assista na última edição os principais memes e virais do programa', imageUrl: img_5 },
        { title: 'Emerson Feffi é o último eliminado do programa no oitavo estouro', imageUrl: img_6 }
      ]
    };
  }
};

</script>

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

.news-section {
  margin-top: 50px;
  padding: 20px;
  font-family: 'Inter', sans-serif;
}

.section-title {
  font-size: 24px;
  font-weight: 600;
  text-align: center;
  margin-bottom: 30px;
  color: #ffffff;
}

.divider {
  width: 80%;
  height: 2px;
  background-color: #ccc;
  margin: 20px auto;
}

.row {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
  gap: 20px;
  flex-wrap: wrap;
}

.col {
  flex: 0 0 calc(33.33% - 20px);
  max-width: calc(33.33% - 20px);
}

.news-item {
  position: relative;
  text-align: center;
  margin-bottom: 20px;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s;
  height: 250px; /* Define a height for news items */
}

.news-item:hover {
  transform: translateY(-5px);
}

.news-image {
  width: 100%;
  height: 100%;
  object-fit: cover; /* Ensure the image covers the entire area without stretching */
}

.news-title {
  position: absolute;
  bottom: 0;
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
