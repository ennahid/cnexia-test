<script setup>
defineProps({
  name: {
    type: String,
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
        <div class="pokemon-img">
          <img :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${id}.png`" />
        </div>
        <p>{{name}}</p>
    </div>
</template>

<style scoped>
.single-pokemon{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    border: 1px solid #cecece;
    height: 100px;
    width: 100px;
    padding: 25px;
    margin: 10px;
}
.single-pokemon .pokemon-img{
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 50px;
    width: 50px;
    margin: 5px;
    background-size: cover;
    background-image: url("https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Pok%C3%A9_Ball_icon.svg/2052px-Pok%C3%A9_Ball_icon.svg.png");
}
.single-pokemon img{
  background-color: #fff;
    /* height: 50px;
    width: 50px;
    margin: 5px; */
    /* background-image: url("https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Pok%C3%A9_Ball_icon.svg/2052px-Pok%C3%A9_Ball_icon.svg.png"); */
}
.single-pokemon p{
  white-space : pre
}
</style>
