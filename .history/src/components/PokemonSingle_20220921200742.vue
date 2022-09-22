<script setup>
defineProps({
  pokemon: {
    type: Object,
    required: true
  },
  id: {
    type: Number,
    required: true
  }
})
</script>

<template>
   <div class="single-pokemon">
     <!-- <img :src="`https://pokeapi.co/media/sprites/items/${id}.png`" /> -->
     <!-- <img :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/home/${id}.png`" /> -->
        <!-- <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Pok%C3%A9_Ball_icon.svg/2052px-Pok%C3%A9_Ball_icon.svg.png" /> -->
        <img :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${id}.png`" />
        <p>{{pokemon.name}}</p>
        <p class="attribue">Height: {{pokemon.height}}</p>
        <p class="attribue">Weight: {{pokemon.weight}}</p>

    </div>
</template>

<style scoped>
.single-pokemon{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    /* border: 1px solid #cecece; */
    border-radius: 6px;
    background-color: #ededff;
    /* height: 150px; */
    width: 150px;
    padding: 25px;
    margin: 10px;
}
.single-pokemon img{
    height: 85px;
    width: 85px;
    margin: 5px;
}
.single-pokemon p{
  font-weight: 600;
  white-space : pre
}
.single-pokemon .attribue{
  background-color: #6b73ab;
  padding: 5px 15px;
  border-radius: 50px;
  margin: 5px;
  color: #fff;
  font-size: 11px;
  font-weight: 400;
  /* width: 100px; */
}
</style>
