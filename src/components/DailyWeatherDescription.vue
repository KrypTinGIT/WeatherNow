<template>
  <div class="weather-description">
    <p>Fühlt sich an wie {{ weather.feelslike }}°C</p>
  </div>
</template>

<script>
export default {
  name: "dailyWeatherDescription",
  props: {
    weather: Object,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.weather-description{
  font-size: 0.7em;
  padding-left: 0.8em;
}

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
