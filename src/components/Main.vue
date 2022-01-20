<template>
<div class="container">
    <ul>
        <li
        v-for="(movie,index) in searchHeader" 
        :key="index"
        >
        <div>{{movie.title}}</div>
        <div>
            {{movie.original_title}}
        </div>
        <div>
        <i :class="(movie.original_language == 'en') ? 'flag flag-us' : `flag flag-${ movie.original_language }`"></i>
        </div>
        <div>
            {{movie.vote_average}}
        </div>
        
        </li>
    </ul>
</div>
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