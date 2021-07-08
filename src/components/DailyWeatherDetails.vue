<template>
  <div class="weather-detail">
    <ul
      data-v-3208ab85=""
      data-v-3e6e9f12=""
      class="weather-items text-container orange-side standard-padding"
    >
      <!---->
      <li>
        <div class="wind-line">
          <svg
            width="30pt"
            height="30pt"
            viewBox="0 0 250 250"
            xmlns="http://www.w3.org/2000/svg"
            xmlns:xlink="http://www.w3.org/1999/xlink"
          >
            <g fill="grey" :transform="'rotate( ' + weather.windDirection + ' 100 100)'"> 
              <polygon id="heart" points="110,10 50,190 110,150 170,190" />
            </g>
          </svg> {{ weather.windSpeed }}m/s {{ weather.windDirection }}Grad
        </div>
      </li>
      <li>
        <span class="symbol">Luftfeuchtigkeit:</span>{{ weather.humidity }} %
      </li>
      <li>
        <span class="symbol">Temperatur:</span>{{ weather.temp }}°C
      </li>
      <li>
        <span class="symbol">Fernsicht:</span>{{ weather.visibility }} m
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
