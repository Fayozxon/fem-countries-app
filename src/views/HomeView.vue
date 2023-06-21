<script>
import data from '../data/data.json';
import Card from '../components/Card.vue';
import Filters from '../components/Filters.vue';

export default {
  components: {Card, Filters},
  data() {
    return {
      filter: '',
      term: ''
    }
  },
  methods: {
    countries() {
      if (this.filter.length && this.term.length) {
        return data.filter(c => c.region.toLowerCase() == this.filter && c.name.toLowerCase().includes(this.term));
      }

      if (this.filter.length) {
        return data.filter(c => c.region.toLowerCase() == this.filter);
      }

      if (this.term.length) {
        return data.filter(c => c.name.toLowerCase().includes(this.term));
      }

      return data;
    },
    setFilter(filter) {
      this.filter = filter;
    },
    setTerm(term) {
      this.term = term;
    }
  }
}
</script>

<template>

  <div class="container">

    <Filters @setFilter="setFilter" @setTerm="setTerm"></Filters>
    
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