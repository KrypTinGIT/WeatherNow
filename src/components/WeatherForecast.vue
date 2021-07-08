<template>
<h2>Forecast</h2>
<table id="forecast-content">
  <tr>
    <td v-for="forecastDay in forecast" :key="forecastDay.timestamp">
        {{ TimestapToDay(forecastDay.timestamp) }} 
        <img v-bind:src="'https://openweathermap.org/img/wn/' + forecastDay.icon + '@2x.png'" />
        {{ forecastDay.temperature }}°C 
    </td>
  </tr>
</table>
</template>

<script>
export default {
  name: "WeatherForecast", 
  methods: {
    TimestapToDay(timestamp) {
      const wochentag = [
        "SO",
        "MO",
        "DI",
        "MI",
        "DO",
        "FR",
        "SA",
      ];
      return wochentag[new Date(timestamp * 1000).getDay()];
    },
  },   
  props: {
    forecast: Array,
  },
};
</script>

<style lang="scss">
  h2{
    padding-left: 1.7em;
  }
  #forecast-content{
    text-align: center;
    padding-left: 2em;
  }
</style>