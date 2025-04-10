<template>
    <div class="initial-coordinates">
      <label for="startX">Start point in X (0-99):</label>
      <input
        type="number"
        id="startX"
        v-model.number="startX"
        :max="99"
        :min="0"
      />
      <label for="startY">Start point in Y (0-34):</label>
      <input
        type="number"
        id="startY"
        v-model.number="startY"
        :max="35"
        :min="0"
      />
      <button @click="setInitialPosition">Establecer posición inicial</button>
    </div>
  </template>
  
 <script>
  export default {
    data() {
      return {
        startX: 50,
        startY: 17,
      };
    },
    methods: {
      setInitialPosition() {
        this.$emit('set-position', { x: this.startX, y: this.startY });
      },
    },
  };
</script>
  
<style>
  .initial-coordinates {
    margin-bottom: 20px;
    background-color: #043f4b;

    label {
        color: white;
    }
  }
  
  .initial-coordinates label {
    margin-right: 10px;
  }
  
  .initial-coordinates input {
    width: 50px;
    margin-right: 10px;
    padding: 5px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .initial-coordinates button {
    padding: 5px 10px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .initial-coordinates button:hover {
    background-color: #45a049;
  }
</style>