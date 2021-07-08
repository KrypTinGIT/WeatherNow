<template>
  <Header title="WeatherNow"/>
  <ApiRead />
  <HelloWorld />
</template>

<script>
import Header from './components/Header.vue'
import ApiRead from './components/ApiRead.vue'

export default {
  name: 'App',
  components: {
    Header,
    ApiRead,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 1em;
}
</style>
