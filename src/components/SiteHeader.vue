<template>
  <header>
    <div class="header-background"></div>
    <div class="header-content">
      <img src="../assets/logo (2).png" alt="Logo" class="logo">
      <button class="hamburger" @click="toggleMobileMenu">
        <span></span>
        <span></span>
        <span></span>
      </button>
      <nav :class="{ open: isMobileMenuOpen }">
        <ul>
          <li class="dropdown" @click="toggleDropdown">
            <a href="#repercussao">Inscrições</a>
            <ul class="dropdown-menu" v-if="isDropdownOpen">
              <li><a href="https://forms.gle/QeZcsHYZTRb3LwB37">A Bolha 2</a></li>
              <li><a href="https://forms.gle/DQoqnMJpcCZYiE1x5">Mete ou Match</a></li>
            </ul>
          </li>
          <li><a href="#episodios">Episódios</a></li>
          <li><a href="#noticias">Notícias</a></li>
        </ul>
      </nav>
    </div>
    <div class="site-description">
      <h1>Acompanhe por aqui!</h1>
      <p>Bem-vindo ao site de A Bolha! Aqui você encontrará informações sobre o reality A Bolha e o próximo grande evento, Mete ou Match. Fique por dentro das inscrições, episódios e últimas notícias.</p>
    </div>
  </header>
</template>

<script>
export default {
  name: 'SiteHeader',
  data() {
    return {
      isDropdownOpen: false,
      isMobileMenuOpen: false,
    };
  },
  methods: {
    toggleDropdown() {
      this.isDropdownOpen = !this.isDropdownOpen;
    },
    toggleMobileMenu() {
      this.isMobileMenuOpen = !this.isMobileMenuOpen;
    },
    closeDropdown() {
      this.isDropdownOpen = false;
    },
    handleOutsideClick(event) {
      if (!this.$el.contains(event.target)) {
        this.isDropdownOpen = false;
        this.isMobileMenuOpen = false;
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
  position: relative;
  top: 0;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 600px;
  justify-content: space-around;
  padding: 1rem;
  z-index: 1000;
  font-family: 'Inter', sans-serif;
  overflow: hidden;
}

.header-background {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 98%;
  height: 100%;
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0.8) 0%, rgba(0, 0, 0, 0) 20%, rgba(0, 0, 0, 0) 80%, rgba(0, 0, 0, 0.8) 100%), 
              url('@/assets/bolha-sabao.jpg') no-repeat center center;
  background-size: cover;
  z-index: -1;
  filter: brightness(0.5);
  border-bottom: 20px solid transparent;
}

.header-background::after {
  content: '';
  position: absolute;
  bottom: -30px;
  left: 50%;
  width: 100%;
  height: 80px;
  background: rgb(0, 0, 0);
  border-radius: 100% 100% 0 0;
  transform: translateX(-50%);
}

.header-content {
  display: flex;
  align-items: center;
  width: 100%;
  justify-content: space-around; /* Garante que a logo e a navegação fiquem em extremidades opostas */
  padding: 0 2rem; /* Espaçamento lateral para dar um pouco de espaço */
  z-index: 1; /* Garante que o conteúdo do cabeçalho fique acima do background */
  padding-bottom: 16rem;
}

.logo {
  height: 50px;
}

nav ul {
  list-style: none;
  display: flex;
  justify-content: space-around;
  margin: 0;
  padding: 0;
}

nav ul li {
  position: relative;
  margin: 0 1rem;
}

nav ul li a {
  color: #fff;
  text-decoration: none;
  padding: 0.5rem 1rem;
}

nav ul li a:hover {
  color: #555;
}

.dropdown-menu {
  display: none;
  position: absolute;
  top: calc(100% + 10px);
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
  white-space: nowrap;
  display: block;
}

.dropdown-menu li a:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

.dropdown .dropdown-menu {
  display: block;
}

.hamburger {
  display: none;
  flex-direction: column;
  justify-content: space-around;
  width: 30px;
  height: 30px;
  background: transparent;
  border: none;
  cursor: pointer;
  z-index: 1002;
}

.hamburger span {
  width: 100%;
  height: 3px;
  background: #fff;
}

@media (max-width: 768px) {
  .hamburger {
    display: flex;
  }

  nav {
    display: none;
    flex-direction: column;
    width: 100%;
    background: rgba(0, 0, 0, 0.9);
    position: absolute;
    top: 60px;
    left: 0;
    z-index: 1001;
  }

  nav.open {
    display: flex;
  }

  nav ul {
    flex-direction: column;
    align-items: center;
  }

  nav ul li {
    margin: 1rem 0;
  }

  .header-content {
     display: flex;
  align-items: center;
  width: 100%;
  justify-content: space-around; /* Garante que a logo e a navegação fiquem em extremidades opostas */

  }
}

.site-description {
  text-align: center;
  color: #fff;
  z-index: 1;
  max-width: 80%;
  border-radius: 10px;
  padding-bottom: 200px;
}

.site-description h1 {
  margin: 0 0 1rem;
}

.site-description p {
  margin: 0;
  font-size: 1.2rem;
  line-height: 1.5;
}
</style>
