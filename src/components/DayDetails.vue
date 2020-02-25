<template lang="html">
  <section v-if="day">
  <h3>📆 Date: {{day.applicable_date}}</h3>
  <div class="row"><div class="column" style="background-color:lightyellow;">
    <p>⛈ Weather: {{day.weather_state_name}}</p>
    <p>➖ Min temperature: {{day.min_temp.toFixed(2)}}°C</p>
    <p>➕ Max temperature: {{day.max_temp.toFixed(2)}}°C</p>
    <p>🧭 Wind direction: {{day.wind_direction_compass}}</p>
  </div>
  <div class="column" style="background-color:lightyellow;">
    <p>💨 Wind speed: {{day.wind_speed.toFixed(2)}} mph</p>
    <p>꩜ Air pressure: {{day.air_pressure.toFixed(1)}} mbar</p>
    <p>💦 Humidity: {{day.humidity}}%</p>
    <p>🌫 Visibility: {{day.visibility.toFixed(2)}} miles</p>
  </div>
</div>


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
 p {
  font-family: sans-serif;

}
h3{
  background-color: grey;
  font-family: sans-serif;
}
section{
  background-color: lightyellow;
}

* {
  box-sizing: border-box;
}

.row {
  display: flex;
}

/* Create two equal columns that sits next to each other */
.column {
  flex: 50%;
  padding: 10px;

}
</style>
