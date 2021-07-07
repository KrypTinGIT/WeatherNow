<template>
  <div class="weather-description">
    <h1>{{ weather.id }}</h1>
    <p>Feels like {{ weather.feelslike }}°C, {{ weather.description }}.</p>
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
