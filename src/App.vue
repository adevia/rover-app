<template>
  <div id="app">
    <WelcomeLogin v-if="!isLoggedIn" @login-success="isLoggedIn = true" />
    <ActualGrid v-else ref="grid" />
  </div>
</template>

<script>
import ActualGrid from './components/Actual-grid.vue'; 
import WelcomeLogin from './components/WelcomeLogin.vue'; 

export default {
  components: {
    ActualGrid,
    WelcomeLogin,
  },
  data() {
    return {
      isLoggedIn: false,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #18738f;
  margin: 0;
}

body {
  margin: 0;
}
</style>