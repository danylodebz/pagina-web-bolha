<template>
  <header>
    <img src="../assets/logo (2).png" alt="Logo" class="logo">
    <nav>
      <ul>
        <li><a href="#episodios">Episódios</a></li>
        <li><a href="#noticias">Notícias</a></li>
        <li><a href="#repercussao">Inscrições</a></li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'SiteHeader'
};
</script>

<style scoped>
header {
  display: flex;
  align-items: center;
  justify-content: space-around;
  padding: 1rem;

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
</style>
