<template>
    <div>
        <h1 align="center">¿Quién es este Pokémon?</h1>
        <PokemonImage :pokemonId="4" :showPokemon="true"/>
        <PokemonOptions :pokemons="pokemonArr"/>
    </div>
</template>

<script>
import PokemonImage from '@/components/PokemonImage.vue'
import PokemonOptions from '@/components/PokemonOptions.vue'
import getPokemonOptions from '@/helpers/getPokemonOptions.js'

export default {
    name: "Pokemon",
    components: {
        PokemonImage,
        PokemonOptions
    },

    data(){
        return{
            pokemonArr: []
        }
    },

    methods:{
        async mixPokemonArray(){
            this.pokemonArr = await getPokemonOptions()
            console.log(this.pokemonArr)
        }
    }, 

    mounted(){
        this.mixPokemonArray()
    }
}
</script>
