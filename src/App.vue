<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <PokemonPage v-bind:id=25 />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import PokemonPage from './components/PokemonPage.vue';

export default {
  name: 'app',
  components: {
    HelloWorld,
    PokemonPage
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
