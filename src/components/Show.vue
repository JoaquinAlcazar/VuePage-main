<template>
    <!-- Código HTML -->
    <div v-if="pokemonToShow != null" class="ShowPokemon">
        <img width="300px" height="300px" v-bind:src="pokemonToShow.sprites.front_default">
        <p>{{ pokemonToShow.name }}</p>
        <p>{{ pokemonToShow.id }}</p>
    </div>
</template>

<script>
//Defincion de componente estilo Option API Vue2+ y Vue3
//import NombreComponente from './components/NombreComponente.vue'
export default {
    props: ['pokemonToShow'],

    name:"show-p",
    data(){
        
    },
    // Lista de funciones (métodos) disponibles en el componente Vue.
    methods: {
        returnInfo(){
            this.$emit('conectaApi', this.pokemonToShow)
        }
    },
};
</script>

<style>
/* Estilos CSS */
</style>