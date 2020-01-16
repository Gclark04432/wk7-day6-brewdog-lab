<template lang="html">
  <div>
    <h1>Beers</h1>
    <beers-names-list :beersNames="beersNames"></beers-names-list>
  </div>
</template>

<script>
import {eventBus} from './main.js';
import BeersNamesList from './components/BeersNamesList.vue';

export default {
  name: 'app',
  data() {
    return {
      beers: [],
      beersNames: [],
      selectedBeer: {}
    }
  },
  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
    .then(result => result.json())
    .then(beers  => {
      this.beersNames = beers.map(beer => beer.name)
    })
    eventBus.$on('name-selected', (selectedBeerName) => {
      this.selectedBeer = selectedBeerName
    })
  },
  components: {
    "beers-names-list": BeersNamesList
  }
}
</script>

<style lang="css" scoped>
</style>
