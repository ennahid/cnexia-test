<script>
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
    }
  },
  // `mounted` is a lifecycle hook which we will explain later
  mounted() {
    // `this` refers to the component instance.
    console.log(this.count) // => 1

    // data can be mutated as well
    this.count = 2
  }
}
</script>

<template>
  
</template>
