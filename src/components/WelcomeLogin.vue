<template>
  <div class="login-container">
    <div class="left-box">
      <img src="@/assets/roverMm.png" alt="Rover" class="bottom-left-image">
    </div>
    <div class="right-box">
      <img src="@/assets/marsLogo.png" alt="Mars Logo" class="logo" />
      <h2>Log In</h2>
      <form @submit.prevent="handleLogin">
        <label for="username">Credential</label>
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
      if (this.username === 'housfy' && this.password === 'frontend') {
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
  display: flex;
  height: 100vh;
}

.left-box {
  flex: 1;
  background-color: #ff610c;
}

.right-box {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: #ffffff;
}

.logo {
  width: 60%;
  max-width: 300px;
  margin-bottom: 20px;
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
    border-bottom: 2px solid #ff610c;
    outline: none;
    transition: border-color 0.3s;
}

input[type="text"]:focus,
input[type="password"]:focus {
    border-bottom: 2px solid #ff610c;
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
    background-color: #0056b3;
}

.error {
  color: red;
}
</style>