<template>
    <div class="background-image-setter">
      <label for="coords">Introduce Coordinates of the arrival point X(0-99) / Y(0-34) </label>
      <label>Arrive point in X (0-99):</label>
      <input type="number" v-model.number="x" min="0" max="99" placeholder="X" />
      <label>Arrive point in X (0-99):</label>
      <input type="number" v-model.number="y" min="0" max="34" placeholder="Y" />
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
        if (this.x >= 0 && this.x <= 99 && this.y >= 0 && this.y <= 34) {
          this.$emit('set-image', { x: this.x, y: this.y });
        } else {
          alert("Please, set correct coordinates within the range X (0-99) / Y (0-34).");
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