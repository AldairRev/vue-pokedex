<template>
  <div class="page">
    <div
      class="page__pattern"
      :style="{ backgroundImage: 'url(./assets/pokeball-pattern.svg)'}"
    >
      <PokemonsList :apiUrl="apiUrl"/>
    </div>
  </div>
  
</template>

<script>
import PokemonsList from './components/PokemonsList.vue';

export default {
  name: 'App',
  components: {
    PokemonsList
  },
  data() {
    return {
      apiUrl: 'https://pokeapi.co/api/v2/pokemon/',
    }
  }
}
</script>

<style lang="scss" src="./assets/scss/app.scss"></style>
