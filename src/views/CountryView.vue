<script>
import { useRoute } from 'vue-router';
import data from '../data/data.json';

export default {
  data() {
    return {
      country: data.find(c => c.name.toLowerCase() === useRoute().params.name)
    }
  },
  methods: {
    goBack() {
      window.history.back();
    }
  }
}
</script>

<template>
  <div class="container">
    <button @click="goBack" class="btn back">
      <i class="fa-solid fa-arrow-left-long"></i>
      Back
    </button>
    <section class="country-section">
      <div class="country-section__img">
        <img :src="country.flag" :alt="`${country.name} flag image`">
      </div>
      <div class="country-section__info">
        <h2 class="country-section__info--title">{{ country.name }}</h2>
        <ul class="country-section__info--texts">
          <li class="country-section__info--text">
            <span>Native name:</span> {{ country.nativeName }}
          </li>
          <li class="country-section__info--text">
            <span>Population:</span> {{ Intl.NumberFormat().format(country.population) }}
          </li>
          <li class="country-section__info--text">
            <span>Region:</span> {{ country.region }}
          </li>
          <li class="country-section__info--text">
            <span>Sub Region:</span> {{ country.subregion }}
          </li>
          <li class="country-section__info--text">
            <span>Capital:</span> {{ country.capital }}
          </li>
          <li class="country-section__info--text">
            <span>Top level domain:</span> <b v-for="domain in country.topLevelDomain">{{ domain+' ' }}</b> 
          </li>
          <li class="country-section__info--text">
            <span>Currencies:</span> <b v-for="currency in country.currencies">{{ currency.code+' ' }}</b> 
          </li>
          <li class="country-section__info--text">
            <span>Languages:</span> <b v-for="language in country.languages">{{ language.name+' ' }}</b>
          </li>
        </ul>
        <p class="country-section__info--text" v-if="country.borders">
          <span>Border Countries:</span>
          <button class="btn border" v-for="border in country.borders">{{ border }}</button>
        </p>
      </div>
    </section>
  </div>
</template>

<style scoped>
.btn {
  background: hsl(209, 23%, 22%);
  border: none;
  color: #fff;
  padding: 10px 30px;
  border-radius: 5px;
  cursor: pointer;
}

main.light .btn {
  background: hsl(0, 0%, 100%);
  color: hsl(200, 15%, 8%);
  box-shadow: 0 5px 15px rgba(0,0,0,0.05);
}

.back {
  margin: 80px 0;
}

.border {
  margin: 10px;
}

.country-section {
  display: flex;
  justify-content: space-between;
  padding-bottom: 120px;
}

.country-section > div {
  width: 45%;
}

.country-section__img img {
  width: 100%;
  box-shadow: 0 5px 15px rgba(0,0,0,0.05);
}

.country-section__info--title {
  font-size: 32px;
  font-weight: 800;
}

.country-section__info--texts {
  padding: 40px 0;
  list-style: none;
  display: flex;
  gap: 5px;
  flex-direction: column;
}

.country-section__info--text span {
  font-weight: 600;
}
</style>