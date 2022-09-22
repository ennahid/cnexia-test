<script>
import axios from 'axios';
export default {
  data() {
    return {
        count: 0,
        pokemonsList : [] 
    }
  },
  methods: {
    increment() {
      this.count++ 
      console.log(this.count) // => 1
    },
    loadPokemons(){
        axios.get('https://pokeapi.co/api/v2/ability/?limit=20&offset=20').then(res => {
        this.pokemonsList = res.data.results;
        console.log(JSON.parse(JSON.stringify(this.pokemonsList)));
        // this.currentpage++;
        });
    }
  },
  // `mounted` is a lifecycle hook which we will explain later
  mounted() {
    // `this` refers to the component instance.
    this.increment()
    this.loadPokemons()
    this.count = 2
    console.log(this.count) // => 1

    // data can be mutated as well
  }
}
</script>

<template>
  <div class="pokemons-list" v-for="pokemon in pokemonsList">
    <PokemonItem pokemon="pokemon.name" />
    </div>
</template>
<style scoped>
.pokemons-list{
    display: flex;
    flex-wrap: wrap;
}
</style>
