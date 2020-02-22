<template lang="html">
<div>
  <ul>
  <country-item  v-for="(country, index) in allCountries" :key="index" :country="country"> </country-item>
</ul>
</div>
</template>


<script>

import CountryItem from './CountryItem.vue';

export default {
  name: 'country-list',
  props: ["allCountries"],
  components: {
    "country-item": CountryItem
  }
}
</script>

<style lang="css" scoped>
</style>
