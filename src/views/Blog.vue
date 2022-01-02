<template>
  <Titulo texto="Titulo de mi Blog" />
    <hr>
    <p v-for="item in arrayBlog" :key="item.id">
        <router-link :to="`/articulo/${item.id}`">
        {{ item.title }}
        </router-link>
    </p>
    <hr>
</template>

<script>
import Titulo from '../components/Titulo.vue'

export default {
  components: { Titulo },
    component:{
        Titulo
    },
    data() {
        return {
            arrayBlog: []
        }
    },
    methods: {
        async consumirAPI(){
            try {
                const data = await fetch('https://jsonplaceholder.typicode.com/posts')
                const array = await data.json()
                this.arrayBlog = array;
            } catch (error) {
                console.log(error);
            }
        }
    },
    created(){
        this.consumirAPI()
    },
}
</script>

<style>

</style>