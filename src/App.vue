<template>
  <div id="app">
    <WelcomeLogin v-if="!isLoggedIn" @login-success="isLoggedIn = true" />
    <ActualGrid v-else ref="grid" />
  </div>
</template>

<script>
import ActualGrid from './components/Actual-grid.vue'; 
import WelcomeLogin from './components/WelcomeLogin.vue'; 

export default {
  components: {
    ActualGrid,
    WelcomeLogin,
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
  font-family: Avenir, Helvetica, Arial, sans-serif; /* Fuente general */
  -webkit-font-smoothing: antialiased; /* Suavizado de texto */
  -moz-osx-font-smoothing: grayscale; /* Suavizado de texto */
  text-align: center; /* Alineación de texto */
  color: #2c3e50; /* Color del texto */
  margin: 0; /* Quitar margen */
}

/* Estilo para eliminar margen del body */
body {
  margin: 0; /* Eliminamos el margen del body */
}
</style>