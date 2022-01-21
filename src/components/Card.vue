<template>
<div class="col">
    <div class="card-item">
        <div class="cont-img">
            <img v-if="poster" :src="image" :alt="title">
            <img v-else src="../assets/movie.png" alt="title">
        </div>
        <div class="info-hover p-3">
            <span>Titolo: {{title}}</span>
            <span>Titolo originale: {{originalTitle}}</span>
            <span>Lingua: <i :class="'flag flag-' + flags(language)"></i></span>
            <!-- <span>Voto: {{fiveStarVote(vote)}}</span> -->
            <div class="vote">
                <span>Voto: </span>
                <span><i v-for="numStar in 5" 
                :key="numStar" 
                :class="(numStar <= fiveStarVote(vote)) ? 'fas fa-star' : 'far fa-star'"></i></span>
            </div>
            <span>Trama: {{overview}}</span>
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
        cursor: pointer;
    }
    span {
        display: block;
        text-align: center;
    }
}
    .card-item:hover .info-hover {
        display: block;
    }
}
</style>