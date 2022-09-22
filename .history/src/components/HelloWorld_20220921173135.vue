<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script>

<template>
   <div class="single-pokemon">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Pok%C3%A9_Ball_icon.svg/2052px-Pok%C3%A9_Ball_icon.svg.png" />
        <Link to={isType ? `/pokemon/type/${pokemon.name}` : `/pokemon/${pokemon.name}`}>{pokemon.name}</Link>
    </div>
</template>

<style scoped>

</style>
