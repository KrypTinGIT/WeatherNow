<template>
<table>
  <tr>
    <td>
      <h1 id="location">{{ weather.id }}</h1>
      <div class="weather-overview">
        <h1><span class="heading">{{ weather.temp }}°C</span></h1>
      </div>
    </td>
    <td>
      <div id="icon">
        <img v-bind:src="'https://openweathermap.org/img/wn/' + weather.icon + '@2x.png'" />
      </div>
    </td>
  </tr>
</table>
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
<style lang="scss">
#location{
  font-size: 2.5em;
}

#icon{
  img{
    padding-top: 5em;
  }
}

#weather-overview{
  h1{
    padding-top: 2em;
  }
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
