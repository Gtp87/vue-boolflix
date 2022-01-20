<template>
<div class="col">
    <div class="card-item">
        <img :src="image" :alt="title">
        <span>Titolo: {{title}}</span>
        <span>Titolo originale: {{originalTitle}}</span>
        <span>Lingua: <i :class="'flag flag-' + flags(language)"></i></span>
        <!-- <span>Voto: {{fiveStarVote(vote)}}</span> -->
        <div class="vote">
            <span>Voto: </span>
            <i v-for="numStar in 5" 
            :key="numStar" 
            :class="(numStar <= fiveStarVote(vote)) ? 'fas fa-star' : 'far fa-star'"></i>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: "Card",
    props: [
        'title',
        'image',
        'originalTitle',
        'language',
        'vote'
    ],
    methods:{
        flags(language) {
            switch(language){
                case 'en':
                    return 'us';
                case 'ja':
                    return 'jp';
                case 'ko':
                    return 'kr';
                case 'zh':
                    return 'cn';
                case 'ur':
                    return 'pk';
                default:
                    return language;
            }
        },
        fiveStarVote(vote) {
            const numStar = parseFloat(vote)
            return Math.round(numStar / 2);
        }
    }
}
</script>

<style lang="scss">
@import "../assets/style.scss";
.col {
    padding: 1em;
    .card-item {
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    border: 2px solid black;
    span {
        text-align: center;
    }
    img {
        width: 100%;
    }
}
}
</style>