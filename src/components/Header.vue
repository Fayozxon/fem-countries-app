<script>

</script>

<template>

  <header class="header">
    <div class="container">
      <a href="/" class="header__title">Where in the world?</a>
      <button class="header__btn" @click="$emit('toggleTheme')">
        <i class="fa-solid fa-moon"></i>
        Dark Mode
      </button>
    </div>
  </header>

</template>

<style scoped>
.header {
  background: #2b3945;
  padding: 30px 0;
}

.header .container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.header__title {
  font-size: 24px;
  font-weight: 800;
  text-decoration: none;
  color: #fff;
}

@media only screen and (max-width: 475px) {
  .header__title {
    font-size: 16px;
  }
}

.header__btn {
  background: transparent;
  border: none;
  color: #fff;
  cursor: pointer;
  font-weight: 600;
}

.header__btn .fa-moon {
  margin-right: 10px;
}

/* light theme */
main.light .header {
    background: hsl(0, 0%, 98%);
    box-shadow: 0 5px 15px rgba(0,0,0,0.05);
}

main.light .header__title, main.light .header__btn {
  color: hsl(200, 15%, 8%);
}
</style>