<template>
    <div>
        <h1 v-if="!pokemon">Espere por favor...</h1>
        <div v-else>
            <h1 align="center">¿Quién es este Pokémon?</h1>
            <PokemonImage :pokemonId="pokemon.id" :showPokemon="showPokemon"/>
            <PokemonOptions :pokemons="pokemonArr" @selection="checkAnswer"/>

            <template v-if="showAnswer">
                <h2>{{message}}</h2>
                <button @click="newPokemon">Nuevo Pokémon</button>
            </template>
                    
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
            showPokemon: false,
            showAnswer: false,
            message: ''
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
            this.showAnswer = true

            if(pokemonId === this.pokemon.id){
                this.message = `Correcto, es ${this.pokemon.name}`
            }
            else{
                this.message = `Upss...era ${this.pokemon.name}`
            }
        },

        newPokemon(){
            this.showAnswer = false,
            this.showPokemon = false,
            this.pokemonArr = [],
            this.pokemon = null,
            this.mixPokemonArray()
        }
    }, 

    mounted(){
        this.mixPokemonArray()
    }
}
</script>

<style scoped>
button{
    background-color: white;
    border-radius: 5px;
    border: 1px solid rgba(0, 0, 0, 0.2);
    cursor: pointer;
    margin-bottom: 10px;
    width: 180px;
    margin-right: 60px;
}

</style>
