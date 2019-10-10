<template lang="html">
  <ul>
    <list-entry v-for="(beer, index) in beers" :beer="beer" :key="index"></list-entry>
  </ul>
</template>

<script>
import ListEntry from './ListEntry.vue';

export default {
  name: 'beer-list',
  props: ['beers'],
  components: {
    'list-entry': ListEntry
  }
}
</script>

<style lang="css" scoped>
</style>
