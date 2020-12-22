<template>
    <div class="container">
        <div class="card" v-if="articulo">
            <div class="card-body">
                <h2> {{ articulo.data.title }} </h2>
                <p class="small"> {{articulo.data.userId}} </p>
                <p> {{ articulo.data.body }} </p>
                <nuxt-link to="/blog" class="btn btn-primary">Atras</nuxt-link>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    data() {
        return {
            articulo: ''
        }
    },
    async created() {
        try{
            const res = await 
            axios.get(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
            this.articulo = res
            console.log(res.data);
        }catch(error) {
            console.log(error);
        }
    }
}
</script>