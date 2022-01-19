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
      valueHeader: null
    }
  },
  methods: {
    getSelect(value) {
      this.valueHeader = value
    }
  },
};
</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap";
</style>
