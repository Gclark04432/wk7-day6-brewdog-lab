<template lang="html">
  <body>
    <beers-names-select :beersNames="beersNames"></beers-names-select>
    <div>
      <beer-detail :selectedBeer="selectedBeer"></beer-detail>
      <favourite-beers :favouriteBeers="favouriteBeers"></favourite-beers>
    </div>
  </body>
</template>

<script>
import {eventBus} from './main.js';
import BeersNamesSelect from './components/BeersNamesSelect.vue';
import BeerDetail from './components/BeerDetail.vue';
import FavouriteBeers from './components/FavouriteBeers';

export default {
  name: 'app',
  data() {
    return {
      beers: [],
      beersNames: [],
      selectedBeer: null,
      favouriteBeers: []
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

    eventBus.$on('favourite-added', (selectedBeer) => {
      this.favouriteBeers.push(selectedBeer)
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
    "beer-detail": BeerDetail,
    "favourite-beers": FavouriteBeers
  }
}
</script>

<style lang="css" scoped>
body {
  background-image: url("../public/background.jpg");
  background-repeat: repeat-x;
  background-size: cover;
  height: 700px;
  background-clip: border-box;
  color: white;
}

div {
  display: grid;
  grid-template-columns: 1fr 1fr;
  justify-content: space-around;
  padding: 20px;
  margin: 20px;
}

beer-detail {
  width: 40%;
}

favourite-beers {
  width: 40%;
}

</style>
