<template lang="html">
  <div v-if="selectedBeer">
    <div>
      <h3>{{ selectedBeer.name }}</h3>
      <p>{{ selectedBeer.description}}</p>
      <p>Alochold by Volume: {{ selectedBeer.abv }}%</p>

      <img :src="selectedBeer.image_url">
      <br>
        <button v-on:click="addToFavourites">Add to favourites</button>
    </div>

  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'beer-detail',
  props: ['selectedBeer'],
  methods: {
    addToFavourites() {
      eventBus.$emit('favourite-added', this.selectedBeer)
    }
  }
}
</script>

<style lang="css" scoped>
  div {
    display: flex;
    flex-direction: column;
    max-width: 600%;
  }

  div img {
    width: 35px;
  }

  h3 {
    text-decoration: underline darkgreen;
  }

</style>
