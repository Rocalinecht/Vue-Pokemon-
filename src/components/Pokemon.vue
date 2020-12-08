<template>
    <div>
        <h1>{{ title }}</h1>
        <div>
            <form @submit.prevent="searchPokemon()">
                <input v-model="pokemonID" placeholder="chose ID ">
                <input type="submit" value="Submit">
            </form>
        </div>
        <div>
            <h2>{{ pokemon.name}}</h2>
              <img
                :src= "pokemon.sprites.front_default" 
                :alt="pokemon.name"  /> 
        </div>
    </div>
</template>

<script>
export default {
  name: 'Pokemon',
  props: {
    title: String
  },
  data(){
      return{
          pokemon:null,
          pokemonID:'',
          errored:false,
          loading: true
      }
  },
  created(){
      this.searchPokemon()
  },
  methods:{

      searchPokemon(){
          fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemonID}`)
           .then(res => res.json())
           .then(data => {
               this.pokemon = data
               this.loading = false
               console.log(data)
           })
        //    .catch(error => console.log(error))
      }
  }
}
</script>