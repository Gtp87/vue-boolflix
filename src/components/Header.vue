<template>
<header>
    <div class="container">
    <div class="row">
        <div class="col-12 d-flex justify-content-between">
            <div class="logo">
                <img src="../assets/boolflix.png" alt="logo">
            </div>
            <div class="d-flex align-items-center">
                <div class="search-container d-flex align-items-center">
                    <input placeholder="Cerca un titolo" @keyup.enter="getMerged" v-model="inputSearch" type="text">
                    <button class="btn btn-light my_btn ms-3" type="submit" @click="getMerged">Cerca</button>
                </div>
            </div>
        </div>
    </div>
</div>
</header>
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
header {
	background-color: #111111;
	.logo {
		width: 20%;
		img {
		width: 100%;
	}
	}
	.search-container {
		height: 30%;
	}
	#search {
		height: 100%;
		font-size: 0.9rem;
	}
	.my_btn {
		font-size: 0.8rem;
		height: 100%;
		padding: 0 1em;
	}
}


</style>