<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
    <h1 class="text-center">Carrusel en Vue.js con Bootstrap</h1>
    <Carousel />
  </nav>
  
</template>


<script>
import Carousel from "./components/Carrusel.vue"; // Asegúrate de que la ruta sea correcta

export default {
  components: {
    Carousel,
  },
};
</script> 

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
