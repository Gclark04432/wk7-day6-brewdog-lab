<template lang="html">
  <div>
    <beers-names-select :beersNames="beersNames"></beers-names-select>
    <beer-detail :selectedBeer="selectedBeer"></beer-detail>
  </div>
</template>

<script>
import {eventBus} from './main.js';
import BeersNamesSelect from './components/BeersNamesSelect.vue';
import BeerDetail from './components/BeerDetail.vue';

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
      this.beers = beers
    })
    eventBus.$on('name-selected', (selectedBeerName) => {
      this.selectedBeer = this.getBeerByName(selectedBeerName)
    })
  },
  methods: {
    getBeerByName(beerName) {
      const foundBeer = this.beers.filter(beer => beer.name === beerName)[0]
      return foundBeer

    }
  },
  components: {
    "beers-names-select": BeersNamesSelect,
    "beer-detail": BeerDetail
  }
}
</script>

<style lang="css" scoped>
  div {
    display: flex;
    justify-content: space-between;
  }
</style>
