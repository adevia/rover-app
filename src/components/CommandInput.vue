<template>
    <div class="command-input">
      <label for="commands">Introduce commands / Example: FFRRFFFRL</label>
      <input type="text" id="commands" v-model="commands" />
      <button @click="executeCommands">GO</button>
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
  
  .command-input label {
    margin-right: 10px;
  }
  
  .command-input input {
    padding: 5px;
    border: 1px solid!important;
    border-radius: 4px;
  }
  
  .command-input button {
    padding: 5px 10px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    margin-top: 10px;
  }
  
  .command-input button:hover {
    background-color: #0056b3;
  }
  </style>