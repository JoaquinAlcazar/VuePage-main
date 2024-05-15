<template>
    <button @click="SendStatus(status)">{{ status }}</button>
</template>

<script>
export default {
    name: "page-Status",
    props: {
        status: null
    },
    methods: {
        SendStatus(status) {
             this.$emit("ChangeStatus",status)
        }
    }
}
</script>

<style scoped>
button {
    border: 0px;
    background-color: aliceblue;
    border-radius: 3px;
    border-bottom: 1px solid rgb(204, 230, 252);
    margin-right: 20px;
}

button:hover {
    background-color: rgb(136, 199, 255);
}


</style>