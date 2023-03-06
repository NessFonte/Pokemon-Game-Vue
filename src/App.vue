<template>
  <div>
    <img class="logo" alt="Vue logo" src="./assets/logo.png">
    <PokemonPage />
  </div>
</template>

<script>
import PokemonPage from './pages/PokemonPage.vue'

export default {
  name: 'App',
  components: {
    PokemonPage
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.logo{
  padding-right: 1500px;
  width: 100px;
}
</style>
