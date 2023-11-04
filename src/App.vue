<template>
  <ZipcodeInput />
</template>

<script>
import ZipcodeInput from './ZipcodeInput';
export default {
  name: 'App',
  components: { ZipcodeInput },
  data() {
    return {
      url: 'https://api.openweathermap.org/data/2.5/weather?zip=94040,us&units=imperial&appid=11a24d1bf1ec4d109feb2851bb6d1c97',
      zipcode: '',
      resultsContainer: '#weather-results',
    }
  },
  methods: {
    handleSubmit() {
      console.log('form submitted')
    },
    fetchWeather() {
      apiKey = '11a24d1bf1ec4d109feb2851bb6d1c97'
      url = `https://api.openweathermap.org/data/2.5/weather?zip=94040,us&units=imperial&appid=${apiKey}`
      fetch(url)
        .then(response => response.json)
        .then(data => console.log(data))
    }
  }
}

</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  margin: 0;
  background: #eee;
}
</style>
