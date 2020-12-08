<template>
  <div id="app">

    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Pokemon title="My Pokemon App"/>

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
