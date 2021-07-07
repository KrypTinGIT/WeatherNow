<template>
<h2>Forecast</h2>
<ol v-for="forecastDay in forecast" :key="forecastDay.timestamp">
    <li> {{ TimestapToDay(forecastDay.timestamp) }} 
        <img v-bind:src="'https://openweathermap.org/img/wn/' + forecastDay.icon + '@2x.png'" />
        {{ forecastDay.temperature }}°C 
    </li>
</ol>
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