<template>
<main>
    <div class="container">
        <div class="row row-cols-5" v-if="searchHeader.films.length > 0">
            <h1>Film</h1>
            <Card v-for="(movie, index) in searchHeader.films" :key="index+'film'" 
            :title="movie.title"
            :originalTitle="movie.original_language"
            :language="movie.original_language"
            :vote="movie.vote_average"
            />
        </div>
        <h3 v-else> Nessun Film Trovato</h3>
        <div class="row row-cols-5" v-if="searchHeader.series.length > 0">
            <h1>Serie TV</h1>
            <Card v-for="(serie, index) in searchHeader.series" :key="index+'series'"
            :title="serie.name"
            :originalTitle="serie.original_name" 
			:language="serie.original_language"
			:vote="serie.vote_average"
            />
        </div>
        <h3 v-else> Nessuna Serie Trovata</h3>
    </div>
</main>

</template>

<script>
import Card from './Card.vue'
export default {
    name:"Main",
    components: {
        Card,
    },

    props: ["searchHeader"],

    data() {
        return {
        }
    },

}
</script>

<style lang="scss">
@import "../assets/style.scss";
</style>