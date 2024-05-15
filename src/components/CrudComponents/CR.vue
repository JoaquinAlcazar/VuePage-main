<!-- eslint-disable vue/no-textarea-mustache -->
<!-- eslint-disable vue/require-v-for-key -->
<template>
    <div>
        <section>
            <article class="table">
                <p class="name">Nombre</p>
                <p class="desc">Description</p>
                <p class="img">fuente de la imagen</p>
            </article>
            <article class="table" id="content">
                <textarea class="name" v-model="name"></textarea>
                <textarea class="desc" v-model="description"></textarea>
                <input type="file" class="img" @change="onFileChange">
            </article>
            <article class="buttons">
                <button>cancelar</button>
                <button>Afegir</button>
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
    data() {
        return {
            copiArray: JSON.parse(JSON.stringify(this.array)),
            name: '',
            description: '',
            image: ''
        }
    },
    methods:
    {
        Add() {

            if (this.array.any(x => x.name == this.name)) {
                alert("El joc ja existeix");
            } else {
                this.ActualizeContent({ name: this.name, description: this.description, image: this.image });
            }
        },
        Cancel(newArray) {
            this.$emit("NewContent", newArray)
        },
        onFileChange(event) {
            const file = event.target.files[0];
            if (file) {
                this.image = URL.createObjectURL(file);
            }
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

.buttons {
    display: flex;
    flex-direction: row;
    padding-left: 30%;
    padding-right: 30%;
    justify-content: space-around;
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

input.img {
    padding-left: 4%;
    padding-top: 1%;

}

.crud {
    width: 200px;
    word-break: break-all;
}
</style>