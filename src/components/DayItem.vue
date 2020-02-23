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

li {
  float: left;
  border-right:1px solid #bbb;
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-family: sans-serif;
  width: 130px;
}

li:hover:not(.active) {
  background-color: #111;
}

.active {
  background-color: #4CAF50;
}

</style>
