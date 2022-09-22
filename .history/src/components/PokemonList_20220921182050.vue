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
        axios.get('https://pokeapi.co/api/v2/ability/?limit=20&offset=20', {
        params: {
            page: this.currentPage + 1
        }
        }).then(res => {
        this.reviews = res.data;
        this.currentpage++;
        });
    }
  },
  // `mounted` is a lifecycle hook which we will explain later
  mounted() {
    // `this` refers to the component instance.
    this.increment()
    this.count = 2
    console.log(this.count) // => 1

    // data can be mutated as well
  }
}
</script>

<template>
  
</template>
