<template>
  <div>
    <InitialCoordinates @set-position="setInitialPosition" />

    <div class="grid">
      <img
        class="rover"
        :style="{ 
          top: (y * 16.67) + 'px',
          left: (x * 16.67) + 'px',
          transition: 'top 0.2s, left 0.2s, transform 0.2s',
          transform: `rotate(${direction * 90}deg)` /* Rotar según dirección */
        }"
        src="@/assets/mars_rover.png"
        alt="Mars Rover"
      />
    </div>

    <div class="coordinates">
      <p>Posición del Rover: ({{ x }}, {{ y }})</p>
    </div>

    <CommandInput @execute-commands="executeCommands" />
  </div>
</template>

<script>
import InitialCoordinates from './InitialCoordinates.vue'; // Asegúrate de que la ruta sea correcta
import CommandInput from './CommandInput.vue'; // Importa el nuevo componente

export default {
  components: {
    InitialCoordinates,
    CommandInput,
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
        this.x = coords.x; // Establecer la posición inicial del rover
        this.y = coords.y;
      } else {
        alert("Por favor, introduce coordenadas válidas dentro del rango (0-29).");
      }
    },
    
    executeCommands(commands) {
      for (const command of commands) {
        switch (command) {
          case 'F': // Movimiento hacia adelante
            this.moveForward();
            break;
          case 'R': // Girar a la derecha
            this.turnRight();
            break;
          case 'L': // Girar a la izquierda
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
.initial-coordinates {
  margin-bottom: 20px; /* Espacio entre el campo de entrada y el tablero */
  font-family: Arial, sans-serif; /* Fuente del texto */
}

.initial-coordinates label {
  margin-right: 10px; /* Espaciado entre la etiqueta y el input */
}

.initial-coordinates input {
  width: 50px; /* Ancho del campo de entrada */
  margin-right: 10px; /* Espaciado entre campos */
  padding: 5px; /* Espaciado interno */
  border: 1px solid #ccc; /* Borde del campo */
  border-radius: 4px; /* Bordes redondeados */
}

.initial-coordinates button {
  padding: 5px 10px; /* Espaciado interno del botón */
  background-color: #4CAF50; /* Color de fondo del botón */
  color: white; /* Color del texto */
  border: none; /* Sin borde */
  border-radius: 4px; /* Bordes redondeados */
  cursor: pointer; /* Cambia el cursor al pasar por encima */
}

.initial-coordinates button:hover {
  background-color: #45a049; /* Color de fondo del botón al pasar el mouse */
}

.grid {
  position: relative;
  width: 500px; /* Tamaño total del tablero */
  height: 500px;
  display: grid;
  grid-template-columns: repeat(30, 1fr); /* 30 columnas */
  grid-template-rows: repeat(30, 1fr); /* 30 filas */
  border: 1px solid black; /* Borde del tablero */
  background: linear-gradient(to right, gray 1px, transparent 1px),
              linear-gradient(to bottom, gray 1px, transparent 1px);
  background-size: 16.67px 16.67px; /* Tamaño de las líneas de la cuadrícula */
}

.rover {
  position: absolute;
  width: 16.67px; /* Tamaño del rover */
  height: 16.67px; /* Tamaño del rover */
  object-fit: contain; /* Asegura que la imagen mantenga su proporción */
  transition: top 0.2s, left 0.2s, transform 0.2s; /* Animación suave para el movimiento y rotación */
}

.coordinates {
  margin-top: 20px; /* Espacio entre el tablero y las coordenadas */
  font-family: Arial, sans-serif; /* Fuente del texto */
  font-size: 16px; /* Tamaño de la fuente */
  color: black; /* Color del texto */
}
</style>