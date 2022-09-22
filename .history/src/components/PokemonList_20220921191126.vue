<script>
import axios from 'axios';
import PokemonSingle from "./PokemonSingle.vue";
export default {
    components: {
        PokemonSingle
    },
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
    loadPokemons(offset = 0){
        axios.get('https://pokeapi.co/api/v2/pokemon?limit=200&offset=0').then(res => {
        this.pokemonsList = [...this.pokemonsList, ...res.data.results];
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
  <div class="pokemons-list">
    <PokemonSingle  v-for="(pokemon, index) in pokemonsList" :id="index + 1"  :name="pokemon.name" />
    </div>
</template>
<style scoped>
.pokemons-list{
    display: flex;
    flex-wrap: wrap;
}
</style>
