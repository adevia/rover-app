<template>
  <div class="container">
    <Logo />

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
import Logo from './Logo-main.vue';

export default {
  components: {
    InitialCoordinates,
    CommandInput,
    Logo,
  },
  data() {
    return {
      x: 50,
      y: 17,
      direction: 0,
    };
  },
  methods: {
    setInitialPosition(coords) {
      if (coords.x >= 0 && coords.x <= 99 && coords.y >= 0 && coords.y <= 34) {
        this.x = coords.x;
        this.y = coords.y;
      } else {
        alert("Por favor, introduce coordenadas válidas dentro del rango X (0-99) / y (0-34).");
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
      switch (this.direction) {
        case 0: // Norte
          if (this.y > 0) this.y--; // Mover hacia arriba
          break;
        case 1: // Este
          if (this.x < 99) this.x++; // Mover hacia la derecha
          break;
        case 2: // Sur
          if (this.y < 34) this.y++; // Mover hacia abajo
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
  display: flex;
  flex-direction: column;
  height: 100vh;
  padding: 10px;
}

.grid-container {
  flex: 3;
  display: flex;
  flex-direction: column;
}

.grid {
  position: relative;
  width: 100%;
  height: 90%;
  display: grid;
  grid-template-columns: repeat(20, 1fr);
  grid-template-rows: repeat(20, 1fr);
  border: 1px solid black;
  background: url('@/assets/background_mars.png') no-repeat center center;
  background-size: cover;
}

.rover {
  position: absolute;
  width: 100px;
  height: 100px;
  object-fit: contain;
  transition: top 0.2s, left 0.2s;
}

.coordinates {
  margin-top: 20px;
  font-size: 2vh;
}

.controls {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
  flex: 1;
}
</style>