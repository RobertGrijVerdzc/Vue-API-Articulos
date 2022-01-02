<template>
    <Titulo texto="Articulos con parametros"/>
    <!-- button @click="consumirAPI()" >Consumir API</button -->
    <h2>Parametro: {{ $route.params.id }}</h2>
    <p>
        {{ arrayBlog.title }}
    </p>
</template>

<script>
    import Titulo from '../components/Titulo.vue'

export default {
    components:{
        Titulo
    },
    data() {
        return {
            arrayBlog: []
        }
    },
    methods: {
        async consumirArticulo(){
            try {
                const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
                const array = await data.json()
                this.arrayBlog = array;
            } catch (error) {
                console.log(error);
            }
        }
    },
    created(){
        this.consumirArticulo()
    },
}
</script>

<style>

</style>