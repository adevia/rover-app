<template>
    <div class="background-image-setter">
      <label for="coords">Introduce Coordinates of the arrival point X(0-99) / Y(0-34) </label>
      <label>Arrive point in X (0-84):</label>
      <input type="number" v-model.number="x" min="0" max="84" placeholder="X" />
      <label>Arrive point in X (0-24):</label>
      <input type="number" v-model.number="y" min="0" max="24" placeholder="Y" />
      <button @click="setBackgroundPosition">Set arrival point</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        x: null,
        y: null,
      };
    },
    methods: {
      setBackgroundPosition() {
        if (this.x >= 0 && this.x <= 84 && this.y >= 0 && this.y <= 24) {
          this.$emit('set-image', { x: this.x, y: this.y });
        } else {
          alert("Please, set correct coordinates within the range X (0-84) / Y (0-24)");
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .background-image-setter {
    margin: 10px 0;
    button{
        margin-top: 10px;
        padding: 5px 10px;
        border: none;
        border-radius: 4px;
    }
  }

  
  </style>