<template>
    <div>
        <h1>{{ title }}</h1>
        <div>
            <form @submit.prevent="getPokemon()">
                <input v-model="pokemonId" placeholder="chose ID ">
                <input type="submit" value="Submit">
            </form>
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
          error:false,
          loading: true
      }
  }
}
</script>