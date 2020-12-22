<template>
  <div class="container">
    <div class="card">
      <div class="card-body my-2" v-for="(item, index) in articulos"
        :key="index"
      >
       <nuxt-link :to="`/blog/${item.id}`">
        <h1> {{ item.title }}  </h1>
       </nuxt-link>
        <p> {{ item.body }} </p>
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data() {
    return {
      articulos: [],
    };
  },
  async created() {
    try {
      const res = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
      this.articulos = res.data
      console.log(res.data);
    } catch(error) {
      console.log(error);
    }

  }
};
</script>
