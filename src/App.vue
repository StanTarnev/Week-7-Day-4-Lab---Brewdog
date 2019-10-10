<template lang="html">
  <div>
    <h1>Brewdog Beers</h1>
    <beer-list :beers="beers"></beer-list>
    <beer-detail :beer="selectedBeer"></beer-detail>
  </div>
</template>

<script>
import {eventBus} from './main.js';
import BeerList from './components/BeerList.vue';
import BeerDetail from  './components/BeerDetail.vue';

export default {
  name: 'app',
  data(){
    return{
      beers: [],
      selectedBeer: null
    }
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(result => result.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer;
    })
  },
  components: {
    'beer-list': BeerList,
    'beer-detail': BeerDetail
  }
}
</script>

<style lang="css" scoped>
</style>
