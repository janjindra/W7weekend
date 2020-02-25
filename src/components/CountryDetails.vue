<template lang="html">
  <section v-if="country" >
  <div class="general">

  <h3>City: {{country.title}}</h3>
    <p>Region: {{country.parent.title}}</p>
    <p>Time zone: {{country.timezone}}</p>
    <p>Current time: {{country.time}}</p>
    <p>Today's sun rise: {{country.sun_rise}}</p>
    <p>Today's sun set: {{country.sun_set}}</p>
    </div>
<br>
    <div>
      <ul>
        <day-item v-for="(day, index) in country.consolidated_weather" :key="index" :day="day"> </day-item>
      </ul>

  </div>

    <!-- <div v-if="selectedDay==null">
      <h3>Date: {{country.consolidated_weather[0].applicable_date}}</h3>
      <p>Weather: {{country.consolidated_weather[0].weather_state_name}}</p>
      <p>Min temperature: {{country.consolidated_weather[0].min_temp}}</p>
      <p>Max temperature: {{country.consolidated_weather[0].max_temp}}</p>
      <p>Wind direction: {{country.consolidated_weather[0].wind_direction_compass}}</p>
      <p>Wind speed: {{country.consolidated_weather[0].wind_speed}}</p>
      <p>Air pressure: {{country.consolidated_weather[0].air_pressure}}</p>
      <p>Humidity: {{country.consolidated_weather[0].humidity}}</p>
      <p>Visibility: {{country.consolidated_weather[0].visibility}}</p>
    </div> -->

    <day-detail :day="selectedDay" v-if="selectedDay"/>

  </section>
</template>

<script>

import DayItem from './DayItem.vue';
import DayDetail from './DayDetails.vue';
import {eventBus} from '../main.js';

export default {
  name: 'country-detail',
  props: ['country'],
  data () {
    return {
      selectedDay: null
    }
  },
  mounted() {

    eventBus.$on('country-selected', () => {
      this.selectedDay = null;
    })

    eventBus.$on('day-selected', (day) => {

      this.selectedDay = day;
    })

  },
  components: {
    "day-item": DayItem,
    "day-detail": DayDetail
  }
}
</script>

<style lang="css" scoped>
.general {
  background-color: lightyellow;
  font-family: sans-serif;
}

ul {
  list-style-type: lower-alpha;
  margin: 30;
  padding: 0;
  overflow: hidden;
  /* background-color: #333; */
  position: center;
  border-color: blue;
  border-width: thick;
  height: 45px;
  background-color: #8FBC8F;

}
</style>
