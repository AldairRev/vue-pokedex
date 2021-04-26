<template>
  <CardList :apiUrl="apiUrl"/>
</template>

<script>
import CardList from './components/CardList.vue';

export default {
  name: 'App',
  components: {
    CardList
  },
  data() {
    return {
      apiUrl: 'https://pokeapi.co/api/v2/pokemon/',
    }
  }
}
</script>

<style lang="scss" src="./assets/scss/app.scss"></style>
