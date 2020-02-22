<template lang="html">
  <div>
    <li v-on:click="handleClick">{{country.title}}</li>
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'country-item',
  props: ['country'],
  methods: {
    handleClick(){
      eventBus.$emit('country-selected', this.country);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
