<template lang="html">
  <ul>
    <li v-on:click="handleClick" v-for="beerName in beersNames" v-model="selectedBeerName">{{beerName}}</li>
  </ul>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'beers-names-list',
  data(){
    return {
      "selectedBeerName": []
    }
  },
  props: ['beersNames'],
  methods: {
    handleClick(){
      eventBus.$emit('name-selected', this.selectedBeerName)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
