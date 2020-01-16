<template lang="html">
  <div v-if="!favouriteBeers.length == 0">
    <ul>
      <h3>Favourite Beers Below</h3>
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
  h3 {
    text-decoration: underline darkgreen;
  }

  li {
    list-style: none;
    padding:5px;
    color: green;
    background-color: white;
    opacity: 0.7;
  }

</style>
