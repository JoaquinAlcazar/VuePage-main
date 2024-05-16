<template>
    <!-- Código HTML -->
    <div class="FavouritePokemon">
        <section v-for="([name, values]) in pokemonFavoritos" v-bind:key="name">
            <img :src="values.sprites.front_default" :alt="name">
            <p>{{ name }}</p>
        </section>
    </div>
</template>

<script>
//Defincion de componente estilo Option API Vue2+ y Vue3
//import NombreComponente from './components/NombreComponente.vue'
export default {
    props: ['pokemonFavoritos'],

    name: "fav-p",
    data() {

    },

    // Lista de funciones (métodos) disponibles en el componente Vue.
    methods: {

    },
};
</script>

<style scoped>
/* Estilos CSS */
section {
    width: 300px;
    display: grid;
    justify-content: center;
}
p{
    text-align: center;
}
div {
    margin-left: 20px;
    display: flex;
  justify-content: center;
  flex-wrap: wrap;
  justify-content: space-around;

}
</style>