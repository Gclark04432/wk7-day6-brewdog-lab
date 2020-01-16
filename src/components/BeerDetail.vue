<template lang="html">
  <div v-if="selectedBeer">
    <div class="">
      <h3>Selected {{ selectedBeer.name }}</h3>
      <p>{{ selectedBeer.description}}</p>
      <p>Alochold by Volume: {{ selectedBeer.abv }}%</p>

      <img :src="selectedBeer.image_url">
    </div>

  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'beer-detail',
  props: ['selectedBeer']
}
</script>

<style lang="css" scoped>
  div {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    max-width: 40%;
  }

  div img {
    width: 40px;
  }

</style>
