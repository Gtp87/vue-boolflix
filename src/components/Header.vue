<template>
  <div class="container-fluid">
          <div class="col-3">
              <input @keyup.enter="getAxios" v-model="inputSearch" type="text">
              <button @click="getAxios">Cerca</button>
          </div>
  </div>
</template>

<script>
import axios from 'axios';


export default {
    name: "Header",
    data() {
        return {
          query: 'https://api.themoviedb.org/3/search/',
          api_key: '7bb7bbc95342fb7ad4cf8fdde2b711f0',
          language: 'en-US',
          inputSearch: "",
          movies: [], 
        }
    },
    methods: {
      getAxios: function () {
          const endpoint = 'movie';
            const parameters = {
                api_key: this.api_key,
                language: this.language,
                query: this.inputSearch,
        }
        axios.get(`${this.query}${endpoint}`, { params: parameters })
          .then(result => {
            this.movies = result.data.results
            this.$emit("sendSelect", this.movies)
            
          })
          .catch(error => {
            console.error(error);               
          })
      }
    },
}
</script>

<style lang="scss">

</style>