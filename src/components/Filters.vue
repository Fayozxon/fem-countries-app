<script>
export default {
    data() {
        return {
            filter: '',
            term: ''
        }
    }
}
</script>

<template>
  <section class="filters-section">
    <form class="container" @submit.prevent>
        <div class="filters-section__search">
            <i class="fa-solid fa-magnifying-glass"></i>
            <input
              type="text"
              placeholder="Search for a country..."
              v-model="term"
              @input="$emit('setTerm', term.toLowerCase())"
            />
        </div>
        <select class="filters-section__filter" v-model="filter" @change="$emit('setFilter', filter)">
            <option value="" selected>All regions</option>
            <option value="africa">Africa</option>
            <option value="americas">America</option>
            <option value="asia">Asia</option>
            <option value="europe">Europe</option>
            <option value="oceania">Oceania</option>
        </select>
    </form>
  </section>
</template>

<style scoped>
.filters-section .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.filters-section__search {
    width: 100%;
    max-width: 480px;
    padding: 0 30px;
    border-radius: 5px;
    background: hsl(209, 23%, 22%);
}

.filters-section__search input {
    padding-left: 15px;
    width: 90%;
    height: 55px;
    font-size: 16px;
    background: transparent;
    border: none;
    outline: none;
    color: #fff;
}

.filters-section__search input::placeholder {
    color: hsl(0, 0%, 80%);
}

.filters-section__filter {
    height: 55px;
    padding: 0 25px;
    outline: none;
    background: hsl(209, 23%, 22%);
    cursor: pointer;
    border: none;
    border-radius: 5px;
    color: #fff;
}

/* light theme */
main.light .filters-section__filter, main.light .filters-section__search {
    background: hsl(0, 0%, 100%);
    color: hsl(200, 15%, 8%);
    box-shadow: 0 5px 15px rgba(0,0,0,0.05);
}

main.light .filters-section__search input {
    color: hsl(200, 15%, 8%);
}

@media only screen and (max-width: 815px) {
    .filters-section .container {
        flex-direction: column;
        align-items: start;
        gap: 20px;
    }
}
</style>