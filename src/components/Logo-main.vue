<template>
    <div class="logo-container">
      <img src="@/assets/mars_visor.png" alt="Logo" class="logo-main" />
    </div>
  </template>
  
  <script>
  export default {
  };
  </script>
  
  <style>
  .logo-container {
    display: flex;
    position: fixed;
    z-index: 1;
  }
  
  .logo-main {
    max-width: 200px;
  }

  .visor {
    max-width: 200px;
    max-height: 150px;
  }
  </style>