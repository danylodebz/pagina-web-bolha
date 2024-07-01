<template>
  <header>
    <img src="../assets/logo (2).png" alt="Logo" class="logo">
    <nav>
      <ul>
       
        <li class="dropdown" @click="toggleDropdown">
          <a href="#repercussao">Inscrições</a>
          <ul class="dropdown-menu" v-if="isDropdownOpen">
            <li><a  href="https://forms.gle/QeZcsHYZTRb3LwB37">A Bolha 2</a></li>
            <li><a href="https://forms.gle/DQoqnMJpcCZYiE1x5">Mete ou Match</a></li>
          </ul>
        </li>
        <li><a href="#episodios">Episódios</a></li>
        <li><a href="#noticias">Notícias</a></li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'SiteHeader',
  data() {
    return {
      isDropdownOpen: false,
    };
  },
  methods: {
    toggleDropdown() {
      this.isDropdownOpen = !this.isDropdownOpen;
    },
    closeDropdown() {
      this.isDropdownOpen = false;
    },
    handleOutsideClick(event) {
      if (!this.$el.contains(event.target)) {
        this.isDropdownOpen = false;
      }
    },
  },
  mounted() {
    document.addEventListener('click', this.handleOutsideClick);
  },
  beforeDestroy() {
    document.removeEventListener('click', this.handleOutsideClick);
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

header {

  top: 0;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-around;
  padding: 1rem;
  background-color: rgba(0, 0, 0, 0.8); /* Ajuste a cor de fundo conforme necessário */
  z-index: 1000; /* Garante que o cabeçalho fique acima de outros elementos */
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2); /* Adiciona uma sombra para destaque */
  font-family: 'Inter', sans-serif; /* Aplica a fonte Inter */
}

.logo {
  height: 50px; /* Ajuste o tamanho conforme necessário */
}

nav ul {
  list-style: none;
  display: flex;
  justify-content: space-around;
  margin: 0;
  padding: 0;
  flex-grow: 1; /* Para ocupar o espaço disponível */
}

nav ul li {
  position: relative; /* Necessário para posicionar o dropdown */
  margin: 0;
}

nav ul li a {
  color: #fff;
  text-decoration: none;
  padding: 0.5rem 1rem;
}

nav ul li a:hover {
  color: #555;
}

/* Estilo para o submenu */
.dropdown-menu {
  display: none; /* Escondido por padrão */
  position: absolute;
  top: calc(100% + 10px); /* Posiciona logo abaixo do link principal */
  left: 0;
  background-color: rgba(0, 0, 0, 0.8);
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  z-index: 1001;
  list-style: none;
  margin: 0;
  padding: 0;
}

.dropdown-menu li a {
  padding: 0.5rem 1rem;
  white-space: nowrap; /* Previne quebras de linha no texto */
  display: block;
}

.dropdown-menu li a:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

/* Mostra o submenu quando isDropdownOpen é true */
.dropdown .dropdown-menu {
  display: block;
}

/* Adiciona espaço no topo do conteúdo para não ficar escondido pelo cabeçalho fixo */
body {
  padding-top: 80px; /* Ajuste conforme a altura do cabeçalho */
}
</style>
