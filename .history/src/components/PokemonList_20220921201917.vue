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
            // this.pokemonsList = [...this.pokemonsList, ...res.data.results];
            res.data.results.map(pokemon => 
                 axios.get(`https://pokeapi.co/api/v2/pokemon/${pokemon.name}`)
                // .then((pokemonInfo) => {
                //     this.pokemonsList.push(pokemonInfo.data)
                //     console.log(JSON.parse(JSON.stringify(this.pokemonsList)));
                // })
            )
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
    <PokemonSingle  v-for="pokemon in pokemonsList" :pokemon="pokemon" />
</div>
<div class="btn-wrapper">
    <button class="btn" @click="() => loadPokemons()">Load more</button>
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
    background-color: #1b2144;
    color: #fff;
    border: 0px;
    padding: 15px;
    border-radius: 6px;
    cursor: pointer;
    font-weight: 600;
}
</style>
