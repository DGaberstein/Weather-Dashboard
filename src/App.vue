<template>
    <div id="app">
      <h1>Weather Dashboard</h1>
      <LocationSearch @search="addLocation" />
      <div class="dashboard">
        <WeatherCard
          v-for="location in locations"
          :key="location.id"
          :location="location"
          @remove="removeLocation"
        />
      </div>
    </div>
  </template>
  
  <script>
  import LocationSearch from './components/LocationSearch.vue';
  import WeatherCard from './components/WeatherCard.vue';
  
  export default {
    name: 'App',
    components: {
      LocationSearch,
      WeatherCard,
    },
    data() {
      return {
        locations: [],
      };
    },
    methods: {
      addLocation(location) {
        if (!this.locations.find(l => l.id === location.id)) {
          this.locations.push(location);
        }
      },
      removeLocation(id) {
        this.locations = this.locations.filter(l => l.id !== id);
      },
    },
  };
  </script>
  
  <style>
  #app {
    font-family: Arial, sans-serif;
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
  }
  
  .dashboard {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
  }
  </style>
  