<template>
    <div class="command-input">
      <label for="commands">Introduce comandos (ej. FFRRFFFRL):</label>
      <input type="text" id="commands" v-model="commands" />
      <button @click="executeCommands">Ejecutar Comandos</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        commands: '', // Campo para ingresar comandos
      };
    },
    methods: {
      executeCommands() {
        // Emitir el evento con los comandos ingresados
        this.$emit('execute-commands', this.commands);
      },
    },
  };
  </script>
  
  <style>
  .command-input {
    margin-top: 20px; /* Espacio entre secciones */
    font-family: Arial, sans-serif; /* Fuente del texto */
  }
  
  .command-input label {
    margin-right: 10px; /* Espaciado entre la etiqueta y el input */
  }
  
  .command-input input {
    padding: 5px; /* Espaciado interno */
    border: 1px solid #ccc; /* Borde del campo */
    border-radius: 4px; /* Bordes redondeados */
  }
  
  .command-input button {
    padding: 5px 10px; /* Espaciado interno del botón */
    background-color: #007BFF; /* Color de fondo del botón */
    color: white; /* Color del texto */
    border: none; /* Sin borde */
    border-radius: 4px; /* Bordes redondeados */
    cursor: pointer; /* Cambia el cursor al pasar por encima */
  }
  
  .command-input button:hover {
    background-color: #0056b3; /* Color de fondo del botón al pasar el mouse */
  }
  </style>