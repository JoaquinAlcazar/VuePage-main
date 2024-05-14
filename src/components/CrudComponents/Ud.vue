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
      <article v-for="(objeto, index) in copiArray" :key="index" class="table" id="content">
        <textarea class="name" v-model="objeto.name"></textarea>
        <textarea class="desc" v-model="objeto.description"></textarea>
        <textarea class="img" v-model="objeto.image"></textarea>
        <p class="crud"><button @click="Delete(objeto)">Borrar</button></p>
        <p class="crud"><button @click="Updated(objeto)">Actualizar</button></p>
      </article>
    </section>
  </div>
</template>F
<script>

export default {
  name: 'Update-Delete',
  props: {
    array: Array,
  },
  data() {
    return {
      copiArray: JSON.parse(JSON.stringify(this.array))

    }
  },
  methods:
  {
    Delete(item) {

      let newArray = this.array.filter(x => x.name != item.name);
      this.ActualizeContent(newArray);
    }, Updated() {

      this.ActualizeContent(this.copiArray)
    },
    ActualizeContent(newArray) {

      this.$emit("NewContent", newArray)
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
