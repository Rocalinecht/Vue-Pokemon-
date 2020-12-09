<template>
  <div>
    <div class="nav">
      <span>Pokemon VueApp</span>
    </div>
    <div id="app">
      
      <Pokemon title="Search your Favorite"
                v-bind:pokemon="pokemon"
                v-bind:loading="loading"
                v-bind:error="error"
                v-bind:visible="visible"
               :show="show"
                />

    </div>
    <footer >
      <span>Make with <a href="https://pokeapi.co/"> pokeapi </a> for <a href="https://www.ctoutvert.com/"> CTOUTVERT </a></span>
    </footer>
  </div>
</template>

<script>

import Pokemon from './components/Pokemon.vue'

export default {
  name: 'App',
  components: {
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
    },
    show: {
      type: Boolean,
      default: () => false
    },
    visible: {
      type: Boolean,
      default: () => false
    }
  }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');

*{margin:0; padding:0;}

body{
  background: linear-gradient(#ffffff, #e4e4e4); 
}

#app {
  font-family: 'Poppins', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 90vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.nav, footer{
  height: 40px;
  display: flex;
  align-items: center;
  font-family: 'Poppins', sans-serif;
}

.nav span{
  margin: 50px ;
  padding-top: 30px ;
  font-size: 1em;
  font-weight: 700;
}

footer{
  background: #d9d9d9;
  justify-content: center;
  font-size: 9px;
}

a{
  text-decoration: none;
  color: #2c3e50;
  font-style:italic ; 
}

a:hover{
  color: blue;
  cursor: pointer;
}

/* MEDIA QUERIES  */
@media screen and (min-width: 200px) and (max-width: 640px) {
  #app{
    height: 750px;
    width: 80%;
    justify-content: center;
  }
  .nav span{
    margin: 5% ;
    padding-top: 10px ;
    font-size: 15px;
  
}
}
</style>
