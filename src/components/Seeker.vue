<template>
    <!-- Código HTML -->
    <div class="SearchBar">
        <input v-model="nameP" type="text" class="textBox">
        <input @click="ReturnValue" type="submit" value=" buscar">
        <input @click="AddToFav" type="submit" value="Añadir a favoritos">
        <input @click="DeleteFav" type="submit" value="Borrar de favoritos">

    </div>
</template>

<script>
//Defincion de componente estilo Option API Vue2+ y Vue3
//import NombreComponente from './components/NombreComponente.vue'
export default {
    name: "seeker-p",
    data() {
        return {
            nameP: null
        }
    },
    // Lista de funciones (métodos) disponibles en el componente Vue.
    methods: {
        ReturnValue() {
            this.$emit('search', this.nameP);
        },
        AddToFav() {
            this.$emit('addFav', this.nameP);
        },
        DeleteFav() {
            this.$emit('deleteFav', this.nameP);
        }
    },
};
</script>

<style scope>
.SearchBar {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    flex-direction: column;
    align-items: center;
}
.SearchBar>*{
    margin-top: 10px;
}

.textBox {
    width: 200px;
}
</style>