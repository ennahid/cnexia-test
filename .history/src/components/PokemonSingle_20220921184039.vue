<script setup>
defineProps({
  name: {
    type: String,
    required: true
  }
})
</script>

<template>
   <div class="single-pokemon">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Pok%C3%A9_Ball_icon.svg/2052px-Pok%C3%A9_Ball_icon.svg.png" />
        <img :src="`https://pokeapi.co/media/sprites/items/${name}.png`" />
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
.single-pokemon img{
    height: 50px;
    width: 50px;
    margin: 5px;
}
.single-pokemon p{
  white-space : pre
}
</style>
