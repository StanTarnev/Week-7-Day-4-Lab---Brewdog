<template lang="html">
  <div>
    <h1>Brewdog Beers</h1>
    <favorite-beers :beers="favoriteBeers"></favorite-beers>
    <beer-list :beers="beers"></beer-list>
    <beer-detail :beer="selectedBeer" class="details"></beer-detail>
  </div>
</template>

<script>
import {eventBus} from './main.js';
import BeerList from './components/BeerList.vue';
import BeerDetail from  './components/BeerDetail.vue';
import FavoriteBeers from './components/FavoriteBeers.vue';

export default {
  name: 'app',
  data(){
    return{
      beers: [],
      selectedBeer: null,
      favoriteBeers: []
    }
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(result => result.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer;
    })
    eventBus.$on('beer-favorited', (beer) => {
      this.favoriteBeers.push(beer);
    })
  },
  components: {
    'beer-list': BeerList,
    'beer-detail': BeerDetail,
    'favorite-beers': FavoriteBeers
  }
}
</script>

<style lang="css" scoped>

h1 {
  text-align: center;
}

</style>
