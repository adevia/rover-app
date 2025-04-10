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
        commands: '',
      };
    },
    methods: {
      executeCommands() {
        this.$emit('execute-commands', this.commands);
      },
    },
  };
  </script>
  
  <style>
  .command-input {
    font-family: Arial, sans-serif;
  }
  
  .command-input label {
    margin-right: 10px;
  }
  
  .command-input input {
    padding: 5px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .command-input button {
    padding: 5px 10px;
    background-color: #007BFF;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .command-input button:hover {
    background-color: #0056b3;
  }
  </style>