<template lang="html">
  <ul>
    <li v-for="beerName in beersNames" :beerName="beerName">{{beerName}}</li>
  </ul>
</template>

<script>
export default {
  name: 'beers-names-list',
  props: ['beersNames']
}
</script>

<style lang="css" scoped>
</style>
