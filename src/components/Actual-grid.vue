<template>
  <div class="container">
    <Logo /> <!-- Integrar el nuevo componente de logo -->

    <div class="grid">
      <img
        class="rover"
        :style="{ top: (y * 16.67) + 'px', left: (x * 16.67) + 'px', transition: 'top 0.2s, left 0.2s' }"
        src="@/assets/mars_rover.png"
        alt="Mars Rover"
      />
    </div>

    <div class="coordinates">
      <p>Actual Position: ({{ x }}, {{ y }})</p>
    </div>

    <div class="controls">
      <InitialCoordinates @set-position="setInitialPosition" />
      <CommandInput @execute-commands="executeCommands" />
    </div>
  </div>
</template>

<script>
import InitialCoordinates from './InitialCoordinates.vue'; 
import CommandInput from './CommandInput.vue'; 
import Logo from './Logo-main.vue'; // Importar el nuevo componente

export default {
  components: {
    InitialCoordinates,
    CommandInput,
    Logo, // Agregar el nuevo componente a la lista de componentes
  },
  data() {
    return {
      x: 15,      // posición inicial en x (centro)
      y: 15,      // posición inicial en y (centro)
      direction: 0, // dirección inicial (0=N, 1=E, 2=S, 3=O)
    };
  },
  methods: {
    setInitialPosition(coords) {
      if (coords.x >= 0 && coords.x <= 29 && coords.y >= 0 && coords.y <= 29) {
        this.x = coords.x;
        this.y = coords.y;
      } else {
        alert("Por favor, introduce coordenadas válidas dentro del rango (0-29).");
      }
    },
    
    executeCommands(commands) {
      for (const command of commands) {
        switch (command) {
          case 'F':
            this.moveForward();
            break;
          case 'R':
            this.turnRight();
            break;
          case 'L':
            this.turnLeft();
            break;
        }
      }
    },

    moveForward() {
      // Mover en la dirección actual
      switch (this.direction) {
        case 0: // Norte
          if (this.y > 0) this.y--; // Mover hacia arriba
          break;
        case 1: // Este
          if (this.x < 29) this.x++; // Mover hacia la derecha
          break;
        case 2: // Sur
          if (this.y < 29) this.y++; // Mover hacia abajo
          break;
        case 3: // Oeste
          if (this.x > 0) this.x--; // Mover hacia la izquierda
          break;
      }
    },

    turnRight() {
      // Girar a la derecha
      this.direction = (this.direction + 1) % 4; // Cambiar dirección
    },

    turnLeft() {
      // Girar a la izquierda
      this.direction = (this.direction + 3) % 4; // Cambiar dirección
    },
  },
};
</script>

<style>
.container {
  display: flex; /* Usar Flexbox para organizar los elementos */
  flex-direction: column; /* Organizar elementos verticalmente */
  height: 100vh; /* Altura completa de la ventana */
  padding: 10px;
}

.grid-container {
  flex: 3; /* Ocupa 3/4 de la altura */
  display: flex;
  flex-direction: column; /* Coloca el tablero y las coordenadas en columna */
}

.grid {
  position: relative;
  width: 100%; /* Ancho total de la cuadrícula */
  height: 90%; /* Ocupar la altura disponible */
  display: grid;
  grid-template-columns: repeat(20, 1fr); /* 20 columnas */
  grid-template-rows: repeat(20, 1fr); /* 20 filas */
  border: 1px solid black; /* Borde del tablero */
  background: url('@/assets/background_mars.png') no-repeat center center; /* Imagen de fondo */
  background-size: cover; /* Ajusta la imagen al tamaño de la cuadrícula */
}

.rover {
  position: absolute;
  width: 100px; /* Tamaño del rover */
  height: 100px; /* Tamaño del rover */
  object-fit: contain; /* Asegura que la imagen mantenga su proporción */
  transition: top 0.2s, left 0.2s; /* Animación suave para el movimiento */
}

.coordinates {
  margin-top: 20px;
  font-size: 2vh;
}

.controls {
  display: flex; /* Uso de Flexbox para alinear los módulos uno al lado del otro */
  justify-content: space-between; /* Espacio entre los módulos de coordenadas y comandos */
  margin-bottom: 20px; /* Espacio entre los controles y el tablero */
  flex: 1; /* Ocupa 1/4 de la altura total */
}
</style>