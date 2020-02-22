<template lang="html">
  <div>
    <country-list :allCountries="allCountries"> </country-list>
    <country-detail :country="selectedCountry" v-if="selectedCountry"/>


  </div>
</template>

<script>
import CountryList from './components/CountryList.vue';
import CountryDetail from './components/CountryDetails.vue';

// import FaveBeers from './components/FaveBeers.vue';
import {eventBus} from './main.js';

export default {
  name: 'app',
  data () {
    return {
      allCountries: [],
      selectedCountry: null
      // selectedDay: null
    };
  },
  mounted() {
    const proxyurl = "https://cors-anywhere.herokuapp.com/";
    const londonurl = "https://www.metaweather.com/api/location/44418/"; // site that doesn’t send Access-Control-*
    fetch(proxyurl + londonurl)
    .then(res => res.json())
    .then(london => this.allCountries.push(london))

    const moscowurl = "https://www.metaweather.com/api/location/2122265/"; // site that doesn’t send Access-Control-*
    fetch(proxyurl + moscowurl)
    .then(res => res.json())
    .then(moscow => this.allCountries.push(moscow))

    const sydneyurl = "https://www.metaweather.com/api/location/1105779/"; // site that doesn’t send Access-Control-*
    fetch(proxyurl + sydneyurl)
    .then(res => res.json())
    .then(sydney => this.allCountries.push(sydney))

    const berlinurl = "https://www.metaweather.com/api/location/638242/"; // site that doesn’t send Access-Control-*
    fetch(proxyurl + berlinurl)
    .then(res => res.json())
    .then(berlin => this.allCountries.push(berlin))

    const sanfranciscourl = "https://www.metaweather.com/api/location/2487956/"; // site that doesn’t send Access-Control-*
    fetch(proxyurl + sanfranciscourl)
    .then(res => res.json())
    .then(sanfrancisco => this.allCountries.push(sanfrancisco))

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country
    });

    eventBus.$on('day-selected', (day) => {
      this.selectedDay = day;
})

  },

  components: {
    "country-list": CountryList,
    "country-detail": CountryDetail

  }
}
</script>

<style lang="css" scoped>
</style>
