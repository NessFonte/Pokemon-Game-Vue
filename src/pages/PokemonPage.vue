<template>
    <div>
        <h1 v-if="!pokemon">Espere por favor...</h1>
        <div v-else>
            <h1 align="center">¿Quién es este Pokémon?</h1>
            <PokemonImage :pokemonId="pokemon.id" :showPokemon="showPokemon"/>
            <PokemonOptions :pokemons="pokemonArr" @selection="checkAnswer"/>
        </div>
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
            pokemonArr: [],
            pokemon: null,
            showPokemon: false
        }
    },

    methods:{
        async mixPokemonArray(){
            this.pokemonArr = await getPokemonOptions()
            
            const random = Math.floor(Math.random() * 4)
            this.pokemon = this.pokemonArr[random]
        },

        checkAnswer(pokemonId){
            this.showPokemon = true
        }
    }, 

    mounted(){
        this.mixPokemonArray()
    }
}
</script>
