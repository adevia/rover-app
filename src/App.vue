<template>
  <div id="app">
    <WelcomeLogin v-if="!isLoggedIn" @login-success="isLoggedIn = true" />
    <ActualGrid v-else ref="grid" />
  </div>
</template>

<script>
import ActualGrid from './components/Actual-grid.vue'; // Importar el componente de la cuadrícula
import WelcomeLogin from './components/WelcomeLogin.vue'; // Asegúrate de la ruta correcta

export default {
  components: {
    ActualGrid,
    WelcomeLogin, // Registra el nuevo componente
  },
  data() {
    return {
      isLoggedIn: false, // Estado de autenticación
    };
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
  margin-top: 60px;
}
</style>