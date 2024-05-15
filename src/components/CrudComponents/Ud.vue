<!-- eslint-disable vue/no-textarea-mustache -->
<!-- eslint-disable vue/require-v-for-key -->
<template>
  <div>
    <section>
      <article class="table">
        <p class="name">Nombre</p>
        <p class="desc">Description</p>
        <p class="img">fuente de la imagen</p>
        <p class="crud">Borrar</p>
        <p class="crud">Actualizar</p>
      </article>
      <article v-for="([title, game]) in copyCurrentArray" class="table" id="content">
        <p class="name">{{ title }}</p>
        <textarea class="desc" v-model="game.description"></textarea>
        <textarea class="img" v-model="game.image"></textarea>
        <p class="crud"><button @click="Delete(title)">Borrar</button></p>
        <p class="crud"><button @click="Updated(title, game)">Actualizar</button></p>
      </article>
    </section>

  </div>
</template>
<script>

export default {
  name: 'Update-Delete',
  props: {
    array: Array,
  },
  computed: {
    copyCurrentArray() {
      console.log(this.array)
      return JSON.parse(JSON.stringify(Array.from(this.array)));
    }
  },
  methods:
  {
    Delete(item) {

      let newArray = this.array.filter(x => x.name != item.name);
      this.ActualizeContent(newArray);
    }, Updated(title, newArray) {

      this.ActualizeContent(title, newArray)
    },
    ActualizeContent(title, newArray) {
      this.$emit("NewContent", title, newArray)
    }
  }
}
</script>

<style scoped>
* {
  padding: 0px;
  margin: 0px;
  word-wrap: break-word;
}

div {
  width: 100%;
  overflow-x: auto;
  display: flex;
  justify-content: space-around;
}

section {
  width: 1500px;
}

p {
  text-align: center;
  display: flex;
  justify-content: center;
  /* Centrar horizontalmente */
  align-items: center;
}

textarea {
  outline: none;
  border: none;
  text-align: center;
  vertical-align: middle;
}

.table {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  margin-left: 5px;
  margin-right: 5px;
  margin-bottom: 1px;
  margin-top: 10px
}

.name {
  width: 200px;
  word-break: break-all;
}

.desc {
  width: 1000px;
  min-height: 75px;
  overflow-y: auto;
  margin-right: 10px;
}

.img {
  width: 200px;
  word-break: break-all;
}

.crud {
  width: 200px;
  word-break: break-all;
}
</style>
