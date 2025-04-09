<template>
  <div class="login-container">
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
      if (this.username === 'admin' && this.password === 'password') {
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
  margin-top: 50px;
  font-family: Arial, sans-serif;
}

.login-container h2 {
  margin-bottom: 20px;
}

.login-container label {
  display: block;
  margin: 5px 0;
}

.login-container input {
  padding: 5px;
  width: 200px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.login-container button {
  padding: 5px 10px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.login-container button:hover {
  background-color: #45a049;
}

.error {
  color: red; /* Color para el mensaje de error */
}
</style>