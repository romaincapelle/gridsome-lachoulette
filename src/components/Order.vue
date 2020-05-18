<template>
  <div id="main">
    <BeerForm @submit="addBeer" />

    <h3 v-if="sortedBeers.length > 0">beer</h3>
    <ul>
      <ListBeer
        v-for="(beer, i) in sortedBeers"
        :key="i"
        :beer="beer"
        @delete="deleteBeer(i)"
      />
    </ul>
  </div>
</template>

<script>
import BeerForm from './BeerForm.vue';
import ListBeer from './ListBeer.vue';

export default {
  name: 'beerList',
  components: {
    BeerForm,
    ListBeer,
  },
  data() {
    return {
      beers: [],
      completed: [],
    };
  },
  computed: {
    sortedBeers() {
      return this.beers.sort((a, b) => a.nombreDeBiere - b.nombreDeBiere);
    },
  },
  methods: {
    addBeer(beer) {
      this.beers.push(beer);
      this.$emit('update:updatedbeers', this.beers);
    },
  },
};
</script>

<style scoped>
h1 {
  text-align: center;
  margin: 40px 0;
}

ul {
  margin: 0;
  padding: 0;
}
</style>
