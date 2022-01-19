<template>
<div class="container-fluid">
  <input id="search" type="text" v-model="inputSearch" name="search">
  <button @click="$emit('doSearch', inputSearch)">Cerca</button>
</div>
</template>

<script>
export default {
    name: "Header",
    props: {
        inputValue: {
            type: String,
        }
    },
    data() {
        return {
            inputSearch:'',
        }
    },
}
</script>

<style lang="scss">
</style>