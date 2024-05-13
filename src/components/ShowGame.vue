<template>
    <section class="container">
        <img :src="image" :alt="'imagen de ' + title">
        <article class="info">
            <h2 class="title">{{ title }}</h2>
            <p class="desc"> {{ description }}</p>
            
        </article>
    </section>
</template>

<script>
export default {
    name: "Show-Image",
    props: {
        image: null,
        title: null,
        description: null
    }

}
</script>

<style scoped>
* {

    display: flex;
    flex-direction: column;
    align-items: center;

}

.container {
    width: 400px;;
    margin-bottom: 20px;
}
.info{
    width: 90%;
    border: 1px solid black;
    border-radius: 4%;
    background-color: rgb(255, 249, 249);

}

img {
    height: 150px;
    margin-bottom: 10px;
}


p {
    overflow-y: auto;
    max-height: 150px;
    margin-left: 5px;
    margin-right: 5px;
    border-radius: 1px;
}

::-webkit-scrollbar {
    width: 0px;
    background: transparent;
    /* make scrollbar transparent */
}
</style>
