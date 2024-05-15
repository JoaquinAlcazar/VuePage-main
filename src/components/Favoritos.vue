<template>
    <!-- Código HTML -->
    <div v-for="pokemon in pokemonFavoritos" class="FavouritePokemon">
        <img :src="pokemon.sprites.front_default" alt="pokemon.name">
        <p>{{ pokemon.name }}</p>
    </div>
</template>

<script>
//Defincion de componente estilo Option API Vue2+ y Vue3
//import NombreComponente from './components/NombreComponente.vue'
export default {
    props: ['pokemonFavoritos'],

    name:"fav-p",
    data(){
    },
    // Lista de funciones (métodos) disponibles en el componente Vue.
    methods: {

    },
};
</script>

<style>
/* Estilos CSS */
</style>