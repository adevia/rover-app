<template>
  <div class="login-container">
    <div class="left-box">
    </div>
    <div class="right-box">
      <img src="@/assets/marsLogo.png" alt="Mars Logo" class="logo" />
      <h2>Iniciar Sesión</h2>
      <form @submit.prevent="handleLogin">
        <label for="username">Usuario:</label>
        <input type="text" id="username" v-model="username" required />

        <label for="password">Contraseña:</label>
        <input type="password" id="password" v-model="password" required />

        <button type="submit">Ingresar</button>
      </form>
      <p v-if="errorMsg" class="error">{{ errorMsg }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: '',
      errorMsg: '',
    };
  },
  methods: {
    handleLogin() {
      // Verificar el usuario y la contraseña
      if (this.username === '1' && this.password === '1') {
        // Emitir el evento de éxito al iniciar sesión
        this.$emit('login-success'); 
      } else {
        this.errorMsg = 'Usuario o contraseña incorrectos.';
      }
    },
  },
};
</script>

<style>
.login-container {
  display: flex; /* Uso de Flexbox para las cajas */
  height: 100vh; /* Ocupa toda la altura de la ventana */
}

.left-box {
  flex: 1; /* Tamaño flexible para la caja izquierda */
  background-color: #ff610c; /* Color de fondo para la caja izquierda */
}

.right-box {
  flex: 1; /* Tamaño flexible para la caja derecha */
  display: flex;
  flex-direction: column; /* Alinear elementos verticalmente */
  align-items: center; /* Centrar horizontalmente */
  justify-content: center; /* Centrar verticalmente */
  background-color: #ffffff; /* Color de fondo para la caja derecha */
}

.logo {
  width: 60%; /* Ajustar el tamaño del logo */
  max-width: 300px; /* Tamaño máximo del logo */
  margin-bottom: 20px; /* Margen inferior del logo */
}

.error {
  color: red; /* Color para el mensaje de error */
}
</style>