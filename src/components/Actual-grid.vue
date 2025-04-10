<template>
  <div class="container">
    <Logo />

    <div class="grid">
      <img
        class="rover"
        :style="{
          top: (y * 16.67) + 'px',
          left: (x * 16.67) + 'px',
          transition: 'top 0.2s, left 0.2s',
          transform: direction === 0 ? 'rotate(0deg)' :
                    direction === 1 ? 'rotate(90deg)' :
                    direction === 2 ? 'rotate(180deg)' :
                    direction === 3 ? 'rotate(270deg)' : ''
        }"
        src="@/assets/mars_rover.png"
        alt="Mars Rover"
      />

      <img
        class="image-setter"
        :style="{
          top: (imagePosition.y * 16.67) + 'px',
          left: (imagePosition.x * 16.67) + 'px',
          display: imageVisible ? 'block' : 'none',
          transition: 'top 0.2s, left 0.2s'
        }"
        src="@/assets/background.png"
        alt="Background Image"
      />

      <div 
        v-for="(obstacle, index) in obstacles" 
        :key="index" 
        class="obstacle"
        :style="{
          top: (obstacle.y * 16.67) + 'px',
          left: (obstacle.x * 16.67) + 'px',
          position: 'absolute',
          display: obstacle.visible ? 'block' : 'none'
        }"
      ></div>
      
    </div>

    <div class="coordinates">
      <p><mark>ROVER Actual Position is ({{ x }}, {{ y }})</mark></p>
    </div>

    <div class="controls">
      <InitialCoordinates @set-position="setInitialPosition" />
      <BackgroundImageSetter @set-image="setImagePosition" />
      <CommandInput @execute-commands="executeCommands" />
    </div>
  </div>
</template>

<script>
import InitialCoordinates from './InitialCoordinates.vue'; 
import CommandInput from './CommandInput.vue'; 
import Logo from './Logo-main.vue';
import BackgroundImageSetter from './BackgroundImageSetter.vue';

export default {
  components: {
    InitialCoordinates,
    CommandInput,
    Logo,
    BackgroundImageSetter,
  },
  data() {
  return {
    x: 42,
    y: 12,
    direction: 0,
    imageVisible: false,
    imagePosition: { x: 0, y: 0 },
    obstacles: [
      { x: 10, y: 4, visible: false },
      { x: 20, y: 20, visible: false},
      { x: 34, y: 6, visible: false },
      { x: 50, y: 20, visible: false },
      { x: 60, y: 16, visible: false },
      { x: 80, y: 2, visible: false },
    ],
  };
},
  methods: {
    setInitialPosition(coords) {
      if (coords.x >= 0 && coords.x <= 84 && coords.y >= 0 && coords.y <= 24) {
        this.x = coords.x;
        this.y = coords.y;
      } else {
        alert("Por favor, introduce coordenadas válidas dentro del rango X (0-84) / y (0-24).");
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
      let newX = this.x;
      let newY = this.y;

      switch (this.direction) {
        case 0: // Norte
          newY--; 
          break;
        case 1: // Este
          newX++; 
          break;
        case 2: // Sur
          newY++; 
          break;
        case 3: // Oeste
          newX--; 
          break;
      }

      // Comprobar si la nueva posición está dentro de los límites
      if (this.isInBounds(newX, newY)) {
        this.x = newX;
        this.y = newY;

        // Comprobar si hay un obstáculo en la nueva posición
        const obstacle = this.obstacles.find(o => o.x === newX && o.y === newY);
        if (obstacle) {
          obstacle.visible = true; // Hacer visible el obstáculo
        }
      } else {
        alert("Movimiento fuera de límites.");
      }
    },

    isInBounds(x, y) {
      return x >= 0 && x <= 84 && y >= 0 && y <= 24;
    },

    turnRight() {
      this.direction = (this.direction + 1) % 4; 
    },

    turnLeft() {
      this.direction = (this.direction + 3) % 4; 
    },

    setImagePosition(coords) {
      this.imagePosition = coords; 
      this.imageVisible = true; 
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
  height: 100%;
  display: grid;
  grid-template-columns: repeat(20, 1fr);
  grid-template-rows: repeat(20, 1fr);
  border: 1px solid black;
  background: url('@/assets/background_mars.png') no-repeat center center;
  background-size: cover;
}

.rover, .image-setter {
  position: absolute;
  width: 100px; 
  height: 100px;
  object-fit: contain;
  transition: top 0.2s, left 0.2s, transform 0.2s;
  transform-origin: center;
}

.obstacle {
  width: 100px; 
  height: 100px; 
  background-color: red; /* Color para distinguir los obstáculos */
  opacity: 0.7; /* Permitir ver el fondo ligeramente */
  border-radius: 50%; /* Forma circular */
}

.coordinates {
  font-size: 2vh;
}

.controls {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
  flex: 1;
}
</style>