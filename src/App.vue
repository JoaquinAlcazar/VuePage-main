<!-- eslint-disable vue/valid-v-for -->
<template>
  <div class="menu">
    <h1>Mi pagina</h1>
    <article class="buttons">
      <navigation v-for="page in pageStatus" :status="page" @ChangeStatus="ChangeStatus"></navigation>
    </article>
  </div>

  <div v-if="page == 'Home'" class="ContentPanel">
    <viewer v-for="([title, game]) in currentContent" class="gamesContent" :title="title"
      :description="game.description" :image="game.image" :key="title">
    </viewer>
  </div>
  <!-- class="contentPanel2" v-if="page == 'CRUD'" -->
  <div class="contentPanel2" v-if="page == 'CRUD'">
    <button v-if="IsFalse" @click="addNew = true" class="add">Nou</button>

    <cr v-if="!IsFalse" :array="currentContent" @AppendArray="Append" @ChangeAdd="ChangeButton"></cr>

    <ud :array="currentContent" @NewContent="ActualizeContent"></ud>

  </div>

  <div v-if="page == 'API'">

    <Seeker @search="ConectaApi" @addFav="AddToFav" @deleteFav="DeleteFav"></Seeker>
    <Show v-if="NotNullPokemon" :pokemonToShow="pokemon"></Show>
    <favoritos :pokemonFavoritos="GetFavoritos"></favoritos>

  </div>
</template>

<script>
import Seeker from "./components/Seeker.vue";
import Show from "./components/Show.vue";
import viewer from '@/components/ShowGame.vue'
import navigation from '@/components/Status.vue'
import ud from '@/components/CrudComponents/Ud.vue'
import cr from "@/components/CrudComponents/CR.vue"
import favoritos from "@/components/Favoritos.vue"
export default {
  components: {
    viewer,
    navigation,
    ud,
    Seeker,
    Show,
    cr,
    favoritos

  },
  data() {
    return {
      content: new Map([
        ['Dead Cells', {
          description: 'Dead Cells es un videojuego híbrido entre el género de exploración de mazmorras o roguelite, y metroidvania, creando su propio género, “roguevania”, desarrollado por el estudio Motion Twin. El juego fue lanzado para PC, Mac, Linux, Playstation 4, Nintendo Switch y Xbox One, siendo lanzado en la plataforma de Steam el 6 de agosto de 2018, bajo la categoría de juego de acción e indie.',
          image: '/src/components/img/Dead Cells.jpg'
        }],
        ['Pokemon XY', {
          description: 'Pokemon XY es una entrega de la franquicia Pokémon desarrollada por Game Freak y distribuida por Nintendo para la consola portátil Nintendo 3DS. Lanzada en 2013, Pokémon XY introdujo la sexta generación de Pokémon, así como nuevas características de juego y gráficos en 3D.',
          image: '/src/components/img/Pokemon.jpg'
        }]
      ]),
      page: 'Home',
      pageStatus: ['Home', 'CRUD', 'API'],
      addNew: false,

      pokemon: null,
      pokemonFav: new Map([])
    }
  },
  computed: {
    NotNullPokemon() {
      return this.pokemon != null
    },
    HasGotPokemon() {

      return this.pokemonFav.length > 0
    },
    IsHome() {
      return this.page == 'Home'
    }, currentContent() {
      return Array.from(this.content);
    },
    IsFalse() {
      return this.addNew == false;
    },
    GetFavoritos() {
      return Array.from(this.pokemonFav)
    }
  },
  methods: {
    ChangeStatus(status) {
      this.page = status
    },
    ConectaApi(pokemonName) {
      this.bValue = !this.bValue;

      fetch("https://pokeapi.co/api/v2/pokemon/" + pokemonName.toLowerCase())
        .then(res => {
          if (res.ok) {
            res.json().then((json) => {
              this.pokemon = json;
            })
          } else {
            throw new Error("")
          }
        })
        .catch((err => {
          console.log(err);
        }))
    },
    AddToFav() {

      this.pokemonFav.set(this.pokemon.name, this.pokemon)

    },
    DeleteFav(pokemonName) {
      this.pokemonFav.delete(pokemonName);
    },
    ActualizeContent(title, value) {
      this.content.set(title, value)

    },
    Append(title, value) {


      this.content.set(title, value)
    },
    ChangeButton(value) {

      this.addNew = value;

    }
  }
}
</script>

<style scoped>
.ContentPanel {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  justify-content: space-around;
}

.add {
  margin-left: 50%;
  width: 90px;
  height: 60px;
}

.ContentPanel2 {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.gamesContent {
  display: flex;
  flex-wrap: wrap;
}

.menu {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-bottom: 10px;
  height: 130px;
  background-color: aliceblue;
}

.buttons {
  position: relative;
  right: 20px;
  margin-right: 5%;
  width: 100%;
  display: flex;
  justify-content: end;
  flex-direction: row;
}

h1 {
  position: relative;
  top: -15px;
  width: auto;
  text-align: center;
  border-bottom: 1px solid rgb(192, 192, 192);
  border-radius: 8%;
}
</style>
