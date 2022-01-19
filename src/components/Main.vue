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
            {{movie.original_language}}
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

<style>

</style>