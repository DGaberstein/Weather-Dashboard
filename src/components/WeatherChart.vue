<template>
    <div class="chart-container">
      <LineChart :chart-data="chartData" :options="chartOptions" />
    </div>
  </template>
  
  <script>
  import { Line as LineChart } from 'vue-chartjs';
  import { Chart as ChartJS, Title, Tooltip, Legend, LineElement, LinearScale, PointElement, CategoryScale } from 'chart.js';
  
  ChartJS.register(Title, Tooltip, Legend, LineElement, LinearScale, PointElement, CategoryScale);
  
  export default {
    name: 'WeatherChart',
    components: {
      LineChart,
    },
    props: {
      location: Object,
    },
    data() {
      return {
        chartData: {
          labels: ['Temperature', 'Humidity', 'Wind Speed'],
          datasets: [
            {
              label: 'Weather Data',
              backgroundColor: 'rgba(75, 192, 192, 0.2)',
              borderColor: 'rgba(75, 192, 192, 1)',
              data: [this.location.main.temp, this.location.main.humidity, this.location.wind.speed],
            },
          ],
        },
        chartOptions: {
          responsive: true,
          maintainAspectRatio: false,
        },
      };
    },
  };
  </script>
  
  <style scoped>
  .chart-container {
    height: 200px;
  }
  </style>
  