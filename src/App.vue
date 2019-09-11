<template>
  <div>
    <h1>Countries</h1>
    <div class="container">
      <country-detail v-bind:country="selectedCountry"></country-detail>
      <countries-list v-bind:countries="countries"></countries-list>
    </div>
  </div>
</template>

<script>
  import CountriesList from './components/CountriesList.vue';
  import CountryDetail from './components/CountryDetail.vue';
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
      'countries-list': CountriesList,
      'country-detail': CountryDetail
    }

  }
</script>

<style>
  h1{
    text-align: center;
  }
  .container {
    display: flex;
    justify-content: space-around;
  }
</style>