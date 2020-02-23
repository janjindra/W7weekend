<template lang="html">
<div>
  <ul>
  <country-item  v-for="(country, index) in allCountries" :key="index" :country="country" ></country-item>
</ul>
</div>
</template>


<script>

import CountryItem from './CountryItem.vue';

export default {
  name: 'country-list',
  props: ["allCountries"],
  data () {
    return {
      images: [
      { url: '../assets/SanFrancisco.jpeg', alt: 'San Francisco' },
      { url: '../assets/London.jpeg', alt: 'London' },
      { url: '../assets/Berlin.jpeg', alt: 'Berlin' },
      { url: '../assets/Moscow.jpeg', alt: 'Moscow' },
      { url: '../assets/Sydney.jpeg', alt: 'Sydney' }
    ]
    }
  },

  components: {
    "country-item": CountryItem
  }
}
</script>

<style lang="css" scoped>

ul {
  list-style-type: lower-alpha;
  margin: 0;
  padding: 0;
  overflow: hidden;
  /* background-color: #333; */
  position: center;
  border-color: blue;
  border-width: thick;
  height: 45px;
  background-color: Grey;

}

</style>
