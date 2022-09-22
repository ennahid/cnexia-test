<script setup>
defineProps({
  pokemon: {
    type: Object,
    required: true
  }
})
</script>

<template>
   <div class="single-pokemon">
      <img :src="pokemon.sprites.front_default" />
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
    border-radius: 6px;
    background-color: #ededff;
    width: 150px;
    padding: 25px;
    margin: 10px;
}
.single-pokemon img{
    /* height: 85px; */
    width: 150px;
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
  margin: 3px;
  color: #fff;
  font-size: 11px;
  font-weight: 400;
  width: 100px;
  text-align: center;
}
</style>
