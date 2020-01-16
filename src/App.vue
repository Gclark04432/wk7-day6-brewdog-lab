<template lang="html">

</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      beers: [],
    }
  },
  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
      .then(result => result.json())
      .then(beers => this.beers = beers)
  }
}
</script>

<style lang="css" scoped>
</style>
