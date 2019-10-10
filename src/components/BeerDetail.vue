<template lang="html">
  <div class="details" v-if="beer">
    <h3>{{beer.name}}</h3>
    <img :src='beer.image_url'/>
    <p>{{beer.description}}</p>
    <p>Goes well with:
      <ul>
        <li v-for="food in beer.food_pairing">{{food}}</li>
      </ul>
    </p>
    <button v-on:click="addToFavorites">Add to Favorite Beers</button>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'beer-detail',
  props: ['beer'],
  methods: {
    addToFavorites() {
      eventBus.$emit('beer-favorited', this.beer)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
