<template>
    <div class="location-search">
      <input v-model="query" @keyup.enter="search" placeholder="Enter city name" />
      <button @click="search">Search</button>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  const API_KEY = 'bd5e378503939ddaee76f12ad7a97608';
  const API_URL = 'http://api.openweathermap.org/data/2.5/forecast?id=524901&appid=';
  
  export default {
    name: 'LocationSearch',
    data() {
      return {
        query: '',
      };
    },
    methods: {
      async search() {
        try {
          const response = await axios.get(API_URL, {
            params: {
              q: this.query,
              appid: API_KEY,
              units: 'metric',
            },
          });
          this.$emit('search', response.data);
          this.query = '';
        } catch (error) {
          console.error('Error fetching weather data:', error);
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .location-search {
    margin-bottom: 20px;
  }
  
  input {
    padding: 5px;
    margin-right: 10px;
  }
  </style>
