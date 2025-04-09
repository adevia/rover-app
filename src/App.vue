<template>
  <div id="app">
    <ActualGrid ref="grid" />
    <button @click="executeCommands">Mover al destino</button> <!-- Agregado para mover el rover -->
  </div>
</template>

<script>
import ActualGrid from './components/Actual-grid.vue'; // Asegúrate de que la ruta sea correcta

export default {
  components: {
    ActualGrid,
  },
  data() {
    return {
      commands: '', // Aquí se puede agregar la lógica para la entrada de comando si lo deseas
    };
  },
  methods: {
    executeCommands() {
      if (this.$refs.grid) {
        this.$refs.grid.moveToDestination(); // Cambia a usar el método correcto
      } else {
        console.error("El componente 'grid' no está referenciado correctamente.");
      }
    },
  },
};
</script>

<style>
/* Estilos generales para el App.vue si es necesario */
</style>