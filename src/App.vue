<template>
  <div>
    <h1>Countries</h1>
    <div>
      <countries-list v-bind:countries="countries"></countries-list>
    </div>
  </div>
</template>

<script>
  import CountriesList from './components/CountriesList.vue';
  import { eventBus } from './main.js';

  export default {
    name: 'app',
    data(){
      return {
        countries: [],
        selectedCountry: null
      }
    },
    mounted(){
      fetch('https://restcountries.eu/rest/v2/all')
      .then(res => res.json())
      .then(countries => this.countries = countries)

      eventBus.$on('country-selected', (country) => {
        this.selectedCountry = country
      })
    },
    components: {
      'countries-list': CountriesList
    }

  }
</script>

<style>

</style>