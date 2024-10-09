<template>
    <div class="weather-card">
      <h2>{{ location.name }}, {{ location.sys.country }}</h2>
      <button class="remove-btn" @click="$emit('remove', location.id)">X</button>
      <p>Temperature: {{ location.main.temp }}°C</p>
      <p>Humidity: {{ location.main.humidity }}%</p>
      <p>Wind: {{ location.wind.speed }} m/s</p>
      <p>Description: {{ location.weather[0].description }}</p>
      <WeatherChart :location="location" />
    </div>
  </template>
  
  <script>
  import WeatherChart from './WeatherChart.vue';
  
  export default {
    name: 'WeatherCard',
    components: {
      WeatherChart,
    },
    props: {
      location: Object,
    },
  };
  </script>
  
  <style scoped>
  .weather-card {
    background-color: #f0f0f0;
    border-radius: 5px;
    padding: 20px;
    width: calc(33.33% - 20px);
    position: relative;
  }
  
  .remove-btn {
    position: absolute;
    top: 10px;
    right: 10px;
    background: none;
    border: none;
    cursor: pointer;
    font-weight: bold;
  }
  </style>
  