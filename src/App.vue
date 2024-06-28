<template>
  <div id="app">
    <SiteHeader />
    <YouTubeCarousel />
    <NewsSection />
  </div>
</template>

<script>
import SiteHeader from './components/SiteHeader.vue';
import YouTubeCarousel from './components/YouTubeCarousel.vue';
import NewsSection from './components/NewsSection.vue';

export default {
  name: 'App',
  components: {
    SiteHeader,
    YouTubeCarousel,
    NewsSection
  },
};
</script>

<style>
body {
  background-color: #000000; 
  margin: 0;
  font-family: Arial, sans-serif;
}

#app {
  text-align: center;
  color: #fff;
}
</style>
