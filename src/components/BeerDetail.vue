<template lang="html">
  <div v-if="beer">
    <h3>{{beer.name}}</h3>
    <img :src='beer.image_url'/>
    <p>{{beer.description}}</p>
    <p>Goes well with:
      <ul>
        <li v-for="food in beer.food_pairing">{{food}}</li>
      </ul>

    </p>
  </div>
</template>

<script>
export default {
  name: 'beer-detail',
  props: ['beer']
}
</script>

<style lang="css" scoped>
</style>
