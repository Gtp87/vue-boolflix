<template>
  <div class="container-fluid">
          <div class="col-3">
              <input @keyup.enter="getMerged" v-model="inputSearch" type="text">
              <button @click="getMerged">Cerca</button>
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
          mergedArray:{
                selectedMovies: [],
                selectedTv: [],
            }, 
        }
    },
        methods: {
        getFilms: function() {
            const endpoint = 'movie';
            const parameters = {
                api_key: this.api_key,
                language: this.language,
                query: this.inputSearch,
            }
            axios.get(`${this.query}${endpoint}`, { params: parameters })
            .then((result) => {
                this.mergedArray.selectedMovies = result.data.results;
            })
            .catch((error) => {
                console.log(error);
            })
        },
        getTv: function() {
            const endpoint = 'tv';
            const parameters = {
                api_key: this.api_key,
                language: this.language,
                query: this.inputSearch,
            }
            axios.get(`${this.query}${endpoint}`, { params: parameters })
            .then((result) => {
                this.mergedArray.selectedTv = result.data.results;
            })
            .catch((error) => {
                console.log(error);
            })
        },
        getMerged: function() {
            this.getFilms();
            this.getTv();
            setTimeout(() => {
                this.$emit('sendSelect', this.mergedArray)          
                
            }, 500);
        }
    }
}
</script>

<style lang="scss">

</style>