<template>
  <div id="app">
    <ActualGrid ref="grid" />
  </div>
</template>

<script>
import ActualGrid from './components/Actual-grid.vue'; // Verifica que la ruta sea correcta

export default {
  components: {
    ActualGrid,
  },
};
</script>

<style>
/* Estilos generales para App.vue, si es necesario */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif; /* Fuente general */
  -webkit-font-smoothing: antialiased; /* Suavizado de texto */
  -moz-osx-font-smoothing: grayscale; /* Suavizado de texto */
  text-align: center; /* Alineación de texto */
  color: #2c3e50; /* Color del texto */
  margin-top: 60px; /* Espacio superior */
}
</style>