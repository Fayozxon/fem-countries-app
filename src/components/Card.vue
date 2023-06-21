<script>
import { useRouter } from 'vue-router';

export default {
  props: ['country'],
  data() {
    return {
      router: useRouter()
    }
  },
  methods: {
    navigateToCountry() {
      this.router.push(`/country/${this.country.name.toLowerCase()}`);
    }
  }
}
</script>

<template>
  <div class="card" @click="navigateToCountry">
    <img :src="country.flag" alt="Flag image" class="card__img">
    <div class="card__info">
      <h2 class="card__info--title">{{ country.name }}</h2>
      <p class="card__info--text"><span>Population</span>: {{ Intl.NumberFormat().format(country.population) }}</p>
      <p class="card__info--text"><span>Region</span>: {{ country.region }}</p>
      <p class="card__info--text"><span>Capital</span>: {{ country.capital }}</p>
    </div>
  </div>
</template>

<style scoped>
.card {
  width: 260px;
  background: hsl(209, 23%, 22%);
  border-radius: 5px;
  overflow: hidden;
  cursor: pointer;
  /* transition: all 200ms ease-in-out; */
}

.card:hover {
  background: hsl(209, 23%, 27%);
}

.card__img {
  width: 100%;
  height: 170px;
  object-fit: cover;
}

.card__info {
  padding: 30px 20px;
}

.card__info--title {
  font-size: 18px;
  font-weight: 800;
  padding-bottom: 20px;
}

.card__info--text {
  font-size: 16px;
  padding: 3px 0;
}

.card__info--text span {
  font-weight: 600;
}

/* light theme */
main.light .card {
    background: hsl(0, 0%, 100%);
    box-shadow: 0 5px 15px rgba(0,0,0,0.05);
}
</style>