<template lang="html">
  <ul>
    <li v-on:click="handleClick(beerName)" v-for="beerName in beersNames">{{beerName}}</li>
  </ul>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'beers-names-list',
  props: ['beersNames'],
  methods: {
    handleClick(beerName){
      eventBus.$emit('name-selected', beerName)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
