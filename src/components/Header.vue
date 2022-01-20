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
          api_key: 'api_key=7bb7bbc95342fb7ad4cf8fdde2b711f0',
          language: 'en-US',
          inputSearch: "",
          movies: [], 
        }
    },
    methods: {
      getAxios: function () {
          
          axios.get("https://api.themoviedb.org/3/search/movie?api_key=7bb7bbc95342fb7ad4cf8fdde2b711f0",
          {
              params: {
                  query: this.inputSearch
              }
          })
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