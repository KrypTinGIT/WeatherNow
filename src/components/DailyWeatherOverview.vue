<template>
  <div id="icon">
    <img v-bind:src="'https://openweathermap.org/img/wn/' + weather.icon + '@2x.png'" />
  </div>
  <div class="weather-overview">
    <span class="heading">{{ weather.temp }}°C</span>
  </div>
</template>

<script>
export default {
  name: "dailyWeatherOverview",
  props: {
    weather: Object,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
