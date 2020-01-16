<template lang="html">
  <div>
    Favourite Beers Below
    <ul>
      <li v-for="beer in favouriteBeers">{{ beer.name }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'favourite-beers',
  props: ['favouriteBeers']
}
</script>

<style lang="css" scoped>
</style>
