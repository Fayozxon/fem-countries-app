<script>
import data from '../data/data.json';
import Card from '../components/Card.vue';
import Filters from '../components/Filters.vue';

export default {
  components: {Card, Filters},
  methods: {
    countries(filter, term) {
      console.log(filter, term);
      if (filter.length) {
        return data.filter(c => c.region.toLowerCase() == filter);
      }
      return data;
    }
  }
}
</script>

<template>

  <div class="container">

    <Filters @getCountries="countries"></Filters>
    
    <section class="cards-section">
      <Card v-for="country in countries('', '')" :country="country"></Card>
    </section>

  </div>

</template>

<style scoped>
.cards-section {
  padding-bottom: 120px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  column-gap: 15px;
  row-gap: 40px;
}

.filters-section {
  padding: 45px 0;
}
</style>