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
      <article v-for="objeto in array" class="table" id="content" >
        <p class="name">{{ objeto.name }}</p>
        <textarea type="text" class="desc" :value="objeto.description"></textarea>
        <p class="img">{{ objeto.image }}</p>
        <p class="crud"><button>Borrar</button></p>
        <p class="crud"><button>Actualizar</button></p>
      </article>
    </section>
  </div>
</template>
<script>
export default {
  name: 'Update-Delete',
  props: {
    array: Array
  },
  methods: {}
}
</script>

<style scoped>
* {
  padding: 0px;
  margin: 0px;
  word-wrap: break-word;
}
div{
  width: 100%;
  overflow-x: auto;
}
section{
  width: 1400px ;

}

p {
  text-align: center;
  display: flex;
  justify-content: center; /* Centrar horizontalmente */
  align-items: center;
}

textarea{
  outline: none;
  border: none;
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
