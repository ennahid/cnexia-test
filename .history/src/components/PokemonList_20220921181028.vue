<script setup>
  data() {
    return {
        count: 0,
        pokemonsList : [] 
    }
  }
  methods: {
    increment() {
      this.count++ 
      console.log(this.count) // => 1

    }
  }
  // `mounted` is a lifecycle hook which we will explain later
  mounted() {
    // `this` refers to the component instance.
    this.increment()
    console.log(this.count) // => 1

    // data can be mutated as well
    this.count = 2
  }
</script>

<template>
  
</template>
