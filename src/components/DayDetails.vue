<template lang="html">
  <section v-if="day">
  <h3>Date: {{day.applicable_date}}</h3>
  <p>Weather: {{day.weather_state_name}}</p>
  <p>Min temperature: {{day.min_temp}}</p>
  <p>Max temperature: {{day.max_temp}}</p>
  <p>Wind direction: {{day.wind_direction_compass}}</p>
  <p>Wind speed: {{day.wind_speed}}</p>
  <p>Air pressure: {{day.air_pressure}}</p>
  <p>Humidity: {{day.humidity}}</p>
  <p>Visibility: {{day.visibility}}</p>
  </section>
</template>

<script>

export default {
  name: 'day-detail',
  props: ['day'],
  data () {
    return {
    }
  },
  methods: {
  },
  components: {
  }
}
</script>

<style lang="css" scoped>

</style>
