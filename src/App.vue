<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Navbar from './components/Navbar.vue';
import Footer from './components/Footer.vue';

</script>
<template>

  <Navbar />

  <div class="main">
    <router-view></router-view>
  </div>

  <Footer />

</template>

<style lang="scss">
body {
  background: rgb(177, 185, 226);
  background: radial-gradient(circle, rgba(177, 185, 226, 1) 0%, rgba(166, 200, 162, 1) 100%);
}

::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: transparent;
}

::-webkit-scrollbar-thumb {
  background-color: rgba(0, 0, 0, 0.2);
  border-radius: 10px;
  
  &:hover {
    background-color: rgba(0, 0, 0, 0.3);
  }
}

</style>
