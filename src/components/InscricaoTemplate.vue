<template>
    <div class="image-button-container">
        
      <div class="image-button-wrapper" v-for="(item, index) in items" :key="index">
        <img :src="item.image" :alt="`Image ${index + 1}`">
        <button @click="handleButtonClick(item.link)">Inscreva-se</button>
      </div>
    </div>
  </template>
  

  <script>
  export default {
    name: "ImageWithButton",
    data() {
      return {
        items: [
          {
            image: require('@/assets/bolha2.jpeg'), // substitua pelo caminho da sua imagem
            link: 'https://forms.gle/QeZcsHYZTRb3LwB37' // substitua pelo link desejado
          },
          {
            image: require('@/assets/meteoumatch.jpeg'), // substitua pelo caminho da sua imagem
            link: 'https://forms.gle/DQoqnMJpcCZYiE1x5' // substitua pelo link desejado
          }
        ]
      };
    },
    methods: {
      handleButtonClick(link) {
        window.location.href = link; // Redireciona para o link
      }
    }
  };
  </script>
  <style scoped>

@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

.{
    font-family: 'Inter', sans-serif; /* Aplica a fonte Inter */
}
  .image-button-container {
    display: flex;
    flex-wrap: wrap; /* Permite que os itens quebrem para a próxima linha em telas menores */
    justify-content: space-around;
    margin-top: 50px;
    margin-bottom: 80px;
   
  }
  
  .image-button-wrapper {
    text-align: center;
    flex: 1 1 calc(50% - 40px); /* Define que cada item ocupará até 50% do contêiner menos uma margem */
    margin: 10px;
    max-width: 35%; /* Ajuste o tamanho máximo conforme necessário */
  }
  
  .image-button-wrapper img {
    width: 100%;
    border-radius: 10px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2); /* Adiciona uma sombra para destaque */
  }
  
  .image-button-wrapper button {
    margin-top: 10px;
    padding: 10px 20px;
    background-color: #007BFF;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    width: 40%;
    font-family: 'Inter', sans-serif;
    font-size: 16px;
   
  }
  
  .image-button-wrapper button:hover {
    background-color: #0056b3;
  }
  
  /* Media queries para responsividade */
  @media (max-width: 768px) {
    .image-button-wrapper {
      flex: 1 1 100%; /* Cada item ocupará 100% do contêiner em telas menores */
      max-width: none; /* Remove o tamanho máximo em telas menores */
    }
  }
  </style>
  