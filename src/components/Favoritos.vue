<template>
    <!-- Código HTML -->
    <div v-for="([name, values]) in pokemonFavoritos" class="FavouritePokemon">
        <img v-bind:src="values.sprites.front_default" alt="pokemon.name">
        <p>{{ name }}</p>
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