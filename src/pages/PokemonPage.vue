<template>
    <div>
        <h1 align="center">¿Quién es este Pokémon?</h1>
        <PokemonImage :pokemonId="5" :showPokemon="true"/>
        <PokemonOptions />
    </div>
</template>

<script>
import PokemonImage from '@/components/PokemonImage.vue'
import PokemonOptions from '@/components/PokemonOptions.vue'
import getPokemonOptions from '@/helpers/getPokemonOptions.js'

console.log(getPokemonOptions())

export default {
    name: "Pokemon",
    components: {
        PokemonImage,
        PokemonOptions
    }
    
}
</script>
