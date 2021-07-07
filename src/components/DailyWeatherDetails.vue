<template>
  <div class="weather-detail">
    <ul
      data-v-3208ab85=""
      data-v-3e6e9f12=""
      class="weather-items text-container orange-side standard-padding"
    >
      <!---->
      <li data-v-3208ab85="">
        <div data-v-3208ab85="" class="wind-line">
          8.8m/s WSW
        </div>
      </li>
      <li data-v-3208ab85="">
        <span data-v-3208ab85="" class="symbol">Humidity:</span>{{ weather.humidity }} %
      </li>
      <li data-v-3208ab85="">
        <span data-v-3208ab85="" class="symbol">UV:</span>4
      </li>
      <li data-v-3208ab85="">
        <span data-v-3208ab85="" class="symbol">Hallo:</span>13°C
      </li>
      <li data-v-3208ab85="">
        <span data-v-3208ab85="" class="symbol">Visibility:</span>{{ weather.visibility }} m
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "dailyWeatherDetails",
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
