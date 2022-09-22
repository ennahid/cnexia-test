<script>
import axios from 'axios';
import PokemonSingle from "./PokemonSingle.vue";
export default {
    components: {
        PokemonSingle
    },
  data() {
    return {
        pokemonsList : [] ,
        pokemonsListLoading: false 
    }
  },
  methods: {
    increment() {
      this.count++ 
      console.log(this.count) // => 1
    },
    loadPokemons(limit){
        this.pokemonsListLoading = true
        axios.get(`https://pokeapi.co/api/v2/pokemon?limit=${limit || 15}&offset=${this.pokemonsList.length}`).then(async (res) => {
            const newPokemons = await Promise.all(res.data.results.map(async pokemon => {
                const { data } = await axios.get(`https://pokeapi.co/api/v2/pokemon/${pokemon.name}`)
                return data
            }))
            this.pokemonsList = [...this.pokemonsList, ...newPokemons];
            this.pokemonsListLoading = false
        });
    }

  },
  // `mounted` is a lifecycle hook which we will explain later
  mounted() {
    // `this` refers to the component instance.
    this.increment()
    this.loadPokemons(50)
    this.count = 2
    console.log(this.count) // => 1

    // data can be mutated as well
  }
}
</script>

<template>
  <div class="pokemons-list">
    <PokemonSingle  v-for="pokemon in pokemonsList" :pokemon="pokemon" />
</div>
<div v-if="pokemonsList.length > 0" class="btn-wrapper">
    <button class="btn" @click="() => loadPokemons()">{{pokemonsListLoading ? "Loading..." : "Load more"}}</button>
</div>
</template>
<style scoped>
.pokemons-list{
    display: flex;
    flex-wrap: wrap;
}
.btn-wrapper{
    width: 100%;
    text-align: center;
    margin-bottom: 15px;
}
.btn-wrapper button{
    background-color: #424983;
    color: #fff;
    border: 0px;
    padding: 15px;
    border-radius: 8px;
    cursor: pointer;
    font-weight: 600;
}
</style>
