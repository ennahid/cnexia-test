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
        offset: 0,
        offsetBy: 5,
        pokemonsList : [] 
    }
  },
  methods: {
    increment() {
      this.count++ 
      console.log(this.count) // => 1
    },
    loadPokemons(limit = null){
        console.log(limit);
        axios.get(`https://pokeapi.co/api/v2/pokemon?limit=${limit || 15}&offset=${this.pokemonsList.length}`).then(res => {
            res.data.results.map(pokemon => {
                axios.get(`https://pokeapi.co/api/v2/pokemon/${pokemon.name}`).then((pokemonInfo) => {
                    this.pokemonsList.push(pokemonInfo)
                    // this.pokemonsList = [...this.pokemonsList, ...res.data.results];
                })
            })
            this.offset = this.offset + this.offsetBy
            console.log(JSON.parse(JSON.stringify(this.pokemonsList)));
        // this.currentpage++;
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
    <PokemonSingle  v-for="(pokemon, index) in pokemonsList" :id="index + 1"  :name="pokemon.name" />
</div>
<div class="btn-wrapper">
    <button class="btn" @click="() => loadPokemons()">click me</button>
</div>
</template>
<style scoped>
.pokemons-list{
    display: flex;
    flex-wrap: wrap;
}
</style>
