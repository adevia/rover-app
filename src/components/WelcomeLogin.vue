<template>
  <div class="login-container">
    <div class="left-box">
      <img src="@/assets/roverMm.png" alt="Rover" class="bottom-left-image">
    </div>
    <div class="right-box">
      <img src="@/assets/marsLogo.png" alt="Mars Logo" class="logo" />
      <h2>Log In</h2>
      <form @submit.prevent="handleLogin">
        <label for="username">Credencial</label>
        <input type="text" id="username" v-model="username" required />

        <label for="password">Password</label>
        <input type="password" id="password" v-model="password" required />

        <button type="submit">Activate</button>
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

.bottom-left-image {
  max-width: 40%;
}

form {
    background-color: white;
    padding: 20px;
    border-radius: 5px;
    max-width: 400px;
}

label {
    display: block;
    margin-bottom: 5px;
    color: #333;
}

input[type="text"],
input[type="password"] {
    width: 100%;
    padding: 10px;
    margin-bottom: 20px;
    border: none;
    border-bottom: 2px solid #ff610c; /* Borde inferior */
    outline: none;
    transition: border-color 0.3s;
}

input[type="text"]:focus,
input[type="password"]:focus {
    border-bottom: 2px solid #ff610c; /* Color del borde al enfocar */
}

button {
    width: 100%;
    padding: 10px;
    background-color: #ff610c;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #0056b3; /* Color del botón al pasar el ratón */
}

.error {
  color: red; /* Color para el mensaje de error */
}
</style>