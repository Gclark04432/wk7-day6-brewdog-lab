<template lang="html">
  <p v-if="selectedBeer">Selected {{ selectedBeer.name }}</p>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'beer-detail',
  props: ['selectedBeer']
}
</script>

<style lang="css" scoped>
</style>
