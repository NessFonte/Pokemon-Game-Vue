<template>
    <div>
        <h1>¿Quién es este Pokémon?</h1>
        <PokemonImage />
        <PokemonOptions />
    </div>
</template>

<script>
import PokemonImage from '@/components/PokemonImage.vue'
import PokemonOptions from '@/components/PokemonOptions.vue'

export default {
    name: "Pokemon",
    components: {
        PokemonImage,
        PokemonOptions
    }
    
}
</script>
