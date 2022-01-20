<template>
<div class="col">
    <div class="card-item">
        <span>Titolo: {{title}}</span>
        <span>Titolo originale: {{originalTitle}}}</span>
        <span>Lingua: <i :class="'flag flag-' + flags(language)"></i></span>
        <span>Voto: {{vote}}</span>
    </div>
</div>
</template>

<script>
export default {
    name: "Card",
    props: [
        'title',
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
        }
    }
}
</script>

<style lang="scss">
.col {
    padding: 1em;
    .card-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    border: 2px solid black;
    span {
        text-align: center;
    }
}
}
</style>