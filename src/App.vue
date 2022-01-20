<template>
  <div id="app">
  <Header 
  @sendSelect="getSelect($event)"
  />
  <Main 
  :searchHeader="valueHeader"
  />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      valueHeader: {
        films:[],
        series:[],
      },
    }
  },
  methods: {
    getSelect(value) {
      this.valueHeader.films = value.selectedMovies;
      this.valueHeader.series = value.selectedTv;
    }
  },
};
</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap";
  @import '~mdb-ui-kit/css/mdb.min.css';
</style>
