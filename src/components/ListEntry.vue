<template lang="html">
  <li v-on:click="handleClick">{{beer.name}}</li>
  <!-- <select v-on:change="handleSelect" v-model="selectedBeer">
    <option disabled value="">Select a Beer...</option>
    <option v-for="beer in beers" :value="beer">{{beer.name}}</option>
  </select> -->
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'list-entry',
  data(){
    return {
      'selectedBeer': {}
    }
  },
  props: ['beer', 'beers'],
  methods: {
    handleClick(){
      eventBus.$emit('beer-selected', this.beer)
    }
    // handleSelect(){
    //   eventBus.$emit('beer-selected', this.selectedBeer)
    // }
  }
}
</script>

<style lang="css" scoped>
</style>
