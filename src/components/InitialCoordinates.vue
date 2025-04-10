<template>
    <div class="initial-coordinates">
      <label for="startX">Coordenada X inicial (0-29):</label>
      <input
        type="number"
        id="startX"
        v-model.number="startX"
        :max="29"
        :min="0"
      />
      <label for="startY">Coordenada Y inicial (0-29):</label>
      <input
        type="number"
        id="startY"
        v-model.number="startY"
        :max="29"
        :min="0"
      />
      <button @click="setInitialPosition">Establecer posición inicial</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        startX: 15, // Valor por defecto para coordenadas iniciales
        startY: 15, // Valor por defecto para coordenadas iniciales
      };
    },
    methods: {
      setInitialPosition() {
        // Emitir el evento con las coordenadas iniciales
        this.$emit('set-position', { x: this.startX, y: this.startY });
      },
    },
  };
  </script>
  
  <style>
  .initial-coordinates {
    margin-bottom: 20px; /* Espacio entre el campo de entrada y el tablero */
    background-color: #043f4b;

    label {
        color: white;
    }
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
  </style>