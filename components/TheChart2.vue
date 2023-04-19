<template>
    <div>
        <ChardData2 v-for="(data, index) in chartData" :key="index" :chart-data="data" :chart-labels="chartLabels" />
    </div>
</template>
  
<script>
import Chart from 'chart.js/auto';
export default {
  data() {
    return {
      chartData: [],
      chartLabels: [],
      isLoading: true, // ajout d'une variable de chargement
    };
  },
  mounted() {
    Promise.all([
      fetch('https://financialmodelingprep.com/api/v3/historical-price-full/GOOG?apikey=9fb2c7e0767d325798293dbd93d429f3').then(response => response.json()),
      fetch('https://financialmodelingprep.com/api/v3/historical-price-full/MMM?apikey=9fb2c7e0767d325798293dbd93d429f3').then(response => response.json()),
      fetch('https://financialmodelingprep.com/api/v3/historical-price-full/AAPL?apikey=9fb2c7e0767d325798293dbd93d429f3').then(response => response.json())
    ])
      .then(dataArray => {
        dataArray.forEach((data, index) => {
          const label = index === 0 ? 'Appel' : index === 1 ? 'Alphabet Inc.':'3M Company' ;
          const chartData = {
            label: label,
            data: data.historical.map(item => item.close),
            backgroundColor: index === 0 ? 'rgba(54, 162, 235, 0.2)' : index === 1 ? 'rgba(255, 99, 132, 0.2)' : 'rgba(255, 206, 86, 0.2)',
            borderColor: index === 0 ? 'rgba(54, 162, 235, 1)' : index === 1 ? 'rgba(255, 99, 132, 1)' : 'rgba(255, 206, 86, 1)',
            borderWidth: 1
          };
          this.chartData.push(chartData);
          if (this.chartLabels.length === 0) {
            this.chartLabels = data.historical.map(item => item.date);
          }
        });
        this.isLoading = false; // mettre à jour la variable de chargement
        this.renderChart();
      })
      .catch(error => {
        console.error('Error:', error);
      });
  },
  methods: {
    renderChart() {
      if (!this.isLoading) { // ne rendre le graphique que si toutes les données sont prêtes
        const ctx = this.$refs.chart.getContext('10d');
        new Chart(ctx, {
          type: 'line',
          data: {
            labels: this.chartLabels,
            datasets: this.chartData
          },
          options: {
            scales: {
              y: {
                beginAtZero: true
              }
            }
          }
        });
      }
    }
  }
};
</script>