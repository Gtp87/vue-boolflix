<template>
<div class="col">
    <div class="card-item">
        <div class="cont-img">
            <img v-if="poster" :src="image" :alt="title">
            <img v-else src="../assets/movie.png" alt="title">
        </div>
        <div class="info-hover p-3">
            <span class="info-title">Titolo: {{title}}</span>
            <span class="info-original">Titolo originale: {{originalTitle}}</span>
            <span class="info-language">Lingua: <i :class="'flag flag-' + flags(language)"></i></span>
            <!-- <span>Voto: {{fiveStarVote(vote)}}</span> -->
            <div class="info-vote">
                <span>Voto: </span>
                <span><i v-for="(numStar) in 5" 
                :key="numStar" 
                :class="(numStar <= fiveStarVote(vote)) ? 'bi-star-fill' : 'bi-star'"></i></span>
            </div>
            <span class="info-overview">Trama: {{(overview != "") ? overview : 'nessuna descrizione'}}</span>
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
        'vote',
        'poster',
        'overview'
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
                case 'hi':
                    return 'in';
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
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.7.2/font/bootstrap-icons.css");
.col {
    padding: 1em;
    .card-item {
        position: relative;
        height: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        border: 1px solid white;
        .cont-img {
            height: 342px;
            overflow: hidden;
        img {
            width: 100%;
        }
    }
    .info-hover {
        position: absolute;
        background-color: black;
        opacity: 0.8;
        display: none;
        width: 100%;
        height: 100%;
        overflow: auto;
        cursor: pointer;
        span {
        display: block;
        text-align: center;
        }
    }
    
}
    .card-item:hover .info-hover {
        display: block;
    }
    [class^=bi-star] {
        color: yellow;
    }
}
</style>