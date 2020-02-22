<template lang="html">
  <div>
    <li v-on:click="handleClickDay">{{day.applicable_date}}</li>

  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'day-item',
  props: ['day'],
  methods: {
    handleClickDay(){
      eventBus.$emit('day-selected', this.day);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
