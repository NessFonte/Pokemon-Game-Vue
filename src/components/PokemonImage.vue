<template>
  <div class="pokemon-container">
    <img class="pokemon-hidden" :src="imgSrc">
    <img class="fade-in" v-if="showPokemon" :src="imgSrc" alt="pokemon">
  </div>
</template>

<script>
export default {
  name: "PokemonImage",
  props:{
    pokemonId:{
      type: Number,
      required: true
    },
    showPokemon:{
      type: Boolean,
      required: true,
      default: false
    }
  },
 
  computed:{
    imgSrc(){
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`
    }
  }
}
</script>

<style scoped>
  /* Pokemon Picture */
  .pokemon-container {
      height: 200px;
  }
  img {
      height: 200px;
      user-select: none;
      -moz-user-select: none;
      -ms-user-select: none;
      -webkit-user-drag: none;
      -webkit-user-select: none;
  }
  .pokemon-hidden {
      filter: brightness(0);
  }
</style>