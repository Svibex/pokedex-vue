<template>
    <h1>HI</h1>
    <ul>
        <li v-for="(pokemon, index) in pokemonList" :key="`poke-${index}`">
            {{ index+1 }}
            {{ pokemon.pokemon_species.name }}
            <img v-if="index<9" :src="`https://assets.pokemon.com/assets/cms2/img/pokedex/full/00${index+1}.png`" :alt="pokemon">
            <img v-else :src="`https://assets.pokemon.com/assets/cms2/img/pokedex/full/0${index+1}.png`" :alt="pokemon">
        </li>
    </ul>
</template>

<script>
    export default {
        data: () => ({
            pokemonList: []
        }),
        async mounted() {
            const pokeData = await fetch('https://pokeapi.co/api/v2/pokedex/2/').then(
                response => response.json()
            )
            this.pokemonList = pokeData.pokemon_entries
        }
    }
</script>

<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    #app {

    }

    li {
        font-size: 25px;
    }
</style>