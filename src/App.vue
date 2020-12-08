<template>
  <div id="app">

    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Pokemon title="My Pokemon App"
              v-bind:pokemon="pokemon"
              v-bind:loading="loading"
              v-bind:error="error"
              />

  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Pokemon from './components/Pokemon.vue'


export default {
  name: 'App',
  components: {
    HelloWorld,
    Pokemon
  },
   props: {
    pokemon: {
      type: Object,
      default: () => {}
    },
    error: {
      type: Boolean,
      default: () => false
    },
    loading: {
      type: Boolean,
      default: () => false
    }
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
</style>
