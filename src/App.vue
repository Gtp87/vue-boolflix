<template>
  <div id="app">
    <div class="container-fluid">
      <Header @doSearch="setSearch($event)" :inputValue="completedQuery" />
      <Main />
    </div>
  </div>
</template>

<script>
import Main from "./components/Main.vue";
import Header from "./components/Header.vue";
export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      completedQuery: '',
      staticApi: 'https://api.themoviedb.org/3/search/movie?api_key=7bb7bbc95342fb7ad4cf8fdde2b711f0&query=',
    }
  },
  methods: {
    setSearch(value) {
      this.completedQuery = this.staticApi + value;
    }
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap"

</style>