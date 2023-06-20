<script>
import { RouterView } from 'vue-router';
import Header from './components/Header.vue';

export default {
  data() {
    return {
      isLightTheme: false
    }
  },
  components: {Header},
  methods: {
    toggleTheme() {
      this.isLightTheme = !this.isLightTheme;
      localStorage.setItem('isLightTheme', this.isLightTheme);
    }
  },
  mounted() {
    const isLightTheme = localStorage.getItem('isLightTheme');

    if (isLightTheme == 'true') this.isLightTheme = true;
  }
}
</script>

<template>

  <main :class="{light: isLightTheme}">

    <Header @toggleTheme="toggleTheme" />
  
    <RouterView />

  </main>
</template>

<style scoped>

</style>