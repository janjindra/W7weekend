<template lang="html">
  <div>
    <weather-header title="WEATHER FORECAST" />
    <weather-header v-if="!allCountries.length" title="LOADING..." />
    <country-list :allCountries="allCountries"> </country-list>
    <country-detail :country="selectedCountry" v-if="selectedCountry"/>
    <weather-footer position="center" end="Source: https://www.metaweather.com/" />

  </div>
</template>

<script>
import CountryList from './components/CountryList.vue';
import CountryDetail from './components/CountryDetails.vue';
import WeatherHeader from './components/WeatherHeader.vue';
import WeatherFooter from './components/WeatherFooter.vue';

// import FaveBeers from './components/FaveBeers.vue';
import {eventBus} from './main.js';

export default {
  name: 'app',
  data () {
    return {
      allCountries: [],
      selectedCountry: null
    };
  },


  methods: {
      getCountries: function() {
        const promises = [1105779, 638242, 2487956, 44418, 2122265].map(num => {
          return fetch(
            `https://cors-anywhere.herokuapp.com/https://www.metaweather.com/api/location/${num}/`
          ).then(res => res.json());
        });

        Promise.all(promises)
          .then(data => {
            const countryData = data.reduce(
              (flat, toFlatten) => flat.concat(toFlatten),
              []
            );
            countryData.forEach(country => (country));
            this.allCountries = countryData;

          })
          .then(() => this.sortCountries("time"));



      },
      sortCountries: function(property) {
        this.allCountries.sort((a, b) => {
          return a[property] < b[property] ? -1 : 1;
        });
      }
    },

    mounted() {
    this.getCountries();

    eventBus.$on('country-selected', (country) => {
    this.selectedCountry = country;
     });

    eventBus.$on('day-selected', (day) => {
    this.selectedDay = day;
    })
  },
  // mounted() {
  //
  //
  //     const proxyurl = "https://cors-anywhere.herokuapp.com/";
  //     const londonurl = "https://www.metaweather.com/api/location/44418/"; // site that doesn’t send Access-Control-*
  //     fetch(proxyurl + londonurl)
  //     .then(res => res.json())
  //     .then(london => this.allCountries.push(london))
  //
  //
  //       const moscowurl = "https://www.metaweather.com/api/location/2122265/"; // site that doesn’t send Access-Control-*
  //       fetch(proxyurl + moscowurl)
  //       .then(res => res.json())
  //       .then(moscow => this.allCountries.push(moscow))
  //
  //
  //         const sydneyurl = "https://www.metaweather.com/api/location/1105779/"; // site that doesn’t send Access-Control-*
  //         fetch(proxyurl + sydneyurl)
  //         .then(res => res.json())
  //         .then(sydney => this.allCountries.push(sydney))
  //
  //
  //           const berlinurl = "https://www.metaweather.com/api/location/638242/"; // site that doesn’t send Access-Control-*
  //           fetch(proxyurl + berlinurl)
  //           .then(res => res.json())
  //           .then(berlin => this.allCountries.push(berlin))
  //
  //
  //             const sanfranciscourl = "https://www.metaweather.com/api/location/2487956/"; // site that doesn’t send Access-Control-*
  //             fetch(proxyurl + sanfranciscourl)
  //             .then(res => res.json())
  //             .then(sanfrancisco => this.allCountries.push(sanfrancisco))
  //
  //
  //               eventBus.$on('country-selected', (country) => {
  //                 this.selectedCountry = country;
  //               });
  //
  //               eventBus.$on('day-selected', (day) => {
  //                 this.selectedDay = day;
  //               })
  //
  //
  //           },

  // mounted() {
  //
  //   if (this.allCountries.length == 0) {
  //     const proxyurl = "https://cors-anywhere.herokuapp.com/";
  //     const londonurl = "https://www.metaweather.com/api/location/44418/"; // site that doesn’t send Access-Control-*
  //     fetch(proxyurl + londonurl)
  //     .then(res => res.json())
  //     .then(london => this.allCountries.push(london)) }
  //
  //     else if (this.allCountries.length == 1) {
  //       const moscowurl = "https://www.metaweather.com/api/location/2122265/"; // site that doesn’t send Access-Control-*
  //       fetch(proxyurl + moscowurl)
  //       .then(res => res.json())
  //       .then(moscow => this.allCountries.push(moscow)) }
  //
  //       else if (this.allCountries.length == 2) {
  //         const sydneyurl = "https://www.metaweather.com/api/location/1105779/"; // site that doesn’t send Access-Control-*
  //         fetch(proxyurl + sydneyurl)
  //         .then(res => res.json())
  //         .then(sydney => this.allCountries.push(sydney)) }
  //
  //         else if (this.allCountries.length == 3) {
  //           const berlinurl = "https://www.metaweather.com/api/location/638242/"; // site that doesn’t send Access-Control-*
  //           fetch(proxyurl + berlinurl)
  //           .then(res => res.json())
  //           .then(berlin => this.allCountries.push(berlin)) }
  //
  //           else if (this.allCountries.length == 4) {
  //             const sanfranciscourl = "https://www.metaweather.com/api/location/2487956/"; // site that doesn’t send Access-Control-*
  //             fetch(proxyurl + sanfranciscourl)
  //             .then(res => res.json())
  //             .then(sanfrancisco => this.allCountries.push(sanfrancisco)) }
  //
  //             else {
  //               eventBus.$on('country-selected', (country) => {
  //                 this.selectedCountry = country;
  //               });
  //
  //               eventBus.$on('day-selected', (day) => {
  //                 this.selectedDay = day;
  //               })
  //
  //           }
  //           },

            components: {
              "country-list": CountryList,
              "country-detail": CountryDetail,
              "weather-header": WeatherHeader,
              "weather-footer": WeatherFooter

            }
          }
          </script>


<style lang="css" scoped>

    div {
      background-image: url("./assets/world.jpeg");
          }

    weather-footer {
        text-align: center;
          }
          </style>
