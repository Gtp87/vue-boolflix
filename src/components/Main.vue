<template>
<main>
    <ul v-if="searchHeader.films.length > 0">
        <li v-for="(movie, index) in searchHeader.films" :key="index+'film'">
            <div>{{movie.title}}</div>
            <div>{{movie.original_title}}</div>
            <div><i :class="(movie.original_language == 'en') ? 'flag flag-us' : `flag flag-${ movie.original_language }`"></i></div>
            <div>{{movie.vote_average}}</div>
        </li>
    </ul>
    <h3 v-else> Nessun Film Trovato</h3>
    <ul v-if="searchHeader.series.length > 0">
        <li v-for="(movie, index) in searchHeader.series" :key="index+'series'">
            <div>{{movie.name}}</div>
            <div>{{movie.original_name}}</div>
            <div><i :class="(movie.original_language == 'en') ? 'flag flag-us' : `flag flag-${ movie.original_language }`"></i></div>
            <div>{{movie.vote_average}}</div>
        </li>
    </ul>
        <h3 v-else> Nessuna Serie Trovata</h3>
</main>

</template>

<script>

export default {
    name:"Main",

    props: ["searchHeader"],

    data() {
        return {
        }
    },

}
</script>

<style lang="scss">

</style>