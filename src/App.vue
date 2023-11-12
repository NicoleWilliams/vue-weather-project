<template>
   <div id="app" class="container">
    <h1>Local Weather</h1>
    <form @submit.prevent="fetchWeather" class="search-form">
      <input v-model="zipcode" type="text" placeholder="Enter ZIP Code" class="search-input">
      <button type="submit" class="search-button">Get Local Weather</button>
    </form>

    <div v-if="weather" class="weather-result">
      <h2>Weather in {{ weather.location.name }}</h2>
      <p>Temperature: {{ weather.current.temp }}°F</p>
      <p>Humidity: {{ weather.current.humidity }}%</p>
      <p>Condiditon: {{ weather.current.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      // url: 'https://api.openweathermap.org/data/2.5/weather?zip=94040,us&units=imperial&appid=11a24d1bf1ec4d109feb2851bb6d1c97',
      zipcode: '',
      weather: null
      // resultsContainer: '#weather-results',
    }
  },
  methods: {
    handleSubmit() {
      console.log('form submitted')
    },
    fetchWeather() {
      apiKey = '11a24d1bf1ec4d109feb2851bb6d1c97'
      url = `https://api.openweathermap.org/data/2.5/weather?zip=${this.zipcode},us&units=imperial&appid=${apiKey}`
      fetch(url)
        .then(response => response.json)
        .then(data => (this.weather = data))
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
