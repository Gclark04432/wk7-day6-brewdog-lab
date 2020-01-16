<template lang="html">
    <select v-on:change="handleSelect" v-model="selectedBeerName">
      <option disabled selected value="">Please select a beer:</option>
      <option  v-for="beerName in beersNames">{{beerName}}</option>
    </select>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'beers-names-select',
  props: ['beersNames'],
  data() {
    return {
      selectedBeerName: ""
    }
  },
  methods: {
    handleSelect(){
      eventBus.$emit('name-selected', this.selectedBeerName)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
