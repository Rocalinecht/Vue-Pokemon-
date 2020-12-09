<template>
    <div class="box">
        <div class="content">
            <h1>{{ title }}</h1>
            <div class="form">
                <form @submit.prevent="searchPokemon()">
                    <input v-model="pokemonID" placeholder="Write  ID Pokemon" class="pokeid">
                    <br><button type="submit" @click="visible = !visible" value="Submit">GO !</button>
                </form>
            </div>
        </div>

        <div  class="name"  >
            <div class="img">
               <img
                v-bind:src= "sprit"
                v-bind:alt="pokemon.name"
                  v-if="visible"
                 />  
            </div>
            <div  class="name-title" >  
                <h2  >{{ pokemon.name}}</h2>  
                <div class="details"   v-if="visible">
                    <a v-on:click="show = !show">More details &rarr;</a>
                    <transition name="fade" v-if="show">
                        <span v-if="show" class="data">
                          <li> Id : # {{  pokemon.id}} </li> 
                          <li> Type : {{pokeType1}} </li>  
                           <li> Weight : {{  pokemon.weight}}g </li> 
                            <li> Height :{{ pokemon.height}}cm </li> 
                             
                        </span>
                    </transition>
                </div>
            </div>
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
          visible: false,
          error:false,
          loading: true,
          show: false,
          pokeType1:[],
           
         
      }
  },
  mounted(){
      this.searchPokemon()   
      this.show   
  },
  methods:{

      searchPokemon(){
          fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemonID}`)
           .then(res => res.json())
           .then(data  => {
               this.pokemon = data
               this.loading = false
               this.sprit =  `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${this.pokemonID}.png`
               this.pokeType1 =  data.types[0].type.name;
               

               console.log(data)
               console.log( data.types[0].type.name )
                
           })
           .catch( err => {
               console.log(err)
               this.loading = false,
               this.error = true
           }     
        )
      },
  }
}
</script>

<style scoped>
 
.box{
    height: 75%;
    width: 70%;
    display: flex;
    flex-direction: row-reverse;
    justify-content: space-around;
    position: relative;
    border-radius: 50px;
    background: #ffffff;
    background-color: #ffffff;
}
/* Title and Form  */
h1{
    font-size: 4.3em;
    padding: 6%;
    padding-right: 10%;
    text-align: start;
}
.name{
    width: 70%;
    display: flex;
    position: relative;
}
.name-title{
    position: absolute;
    top:55%;
    left:40%;
    text-align:start;  
}
/* DATA  */
h2{
    font-size: 3.5em;
}
span{
    font-size: 2em;
}

.img{
    height: 450px;
    width: 375px;
    background-color: #f5f5f5 ;
    margin-left: 55px;
    bottom: 75px;
    border-radius: 25px;
    position: absolute;
    background: #e6e6e6;
    box-shadow: -29px 29px 48px #c4c4c4, 
                9px -9px 48px #ffffff;
}

img{
    width :350px;
    height: 350px; 
}
.details{
    height: 200px;
    display: flex;
    flex-direction: column;
}

.data{
    font-size: 15px;
    padding-left:35px;
}

.form{
    height: 30%;
    display: flex;
    padding: 6%;
    text-align: start;   
}

input{
    border-radius: 30px;
    background: #e6e6e6;
    border:none;
    height: 40px;
    width: 300px;
    text-align: start;
    padding-right: 2%; 
}

.pokeid {
    padding-left: 30px;
    border-radius: 15px;
    font-style: italic;
}

button {
    outline: none;
    border:none;
    cursor: pointer;
    width:40%;
    height: 45px;
    margin-top: 5%;
    border-radius: 30px;
    font-size: 20px;
    font-weight: 700;
    color:#fff;
    text-align: center;
    background: #9FA5D5;
    box-shadow: 3px 3px 8px #b1b1b1,
                -3px -3px 8px #ffffff;
}

@media screen and (min-width: 200px) and (max-width: 375px) {
  .box {
    flex-direction: column;
    height: 550px;
    width: 250px;
    border-radius: 20px;
  }
  .img{
      width: 300px;
      height: 230px;
      position: static;
      margin: 0;
      left: 5%;
  }
  img{
      height: 150px;
      width: 150px;
  }
  h1{
      font-size: 2.5em;
      padding-top: 20px;
  }
  input{
      width: 175px;
  }
  .name{
      width: 70%;
      margin-left: 40px;
  }
  h2{
      font-size: 2em;
  }
  span{
      font-size: 1em;
  }
}
</style>