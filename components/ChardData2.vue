<template>
    <div>
      <canvas ref="chart" :style="{width: width, height: height}"></canvas>
    </div>
  </template>
  
  <script>
  import Chart from 'chart.js/auto';
  
  export default {
    props: {
      chartData: {
        type: Object,
        required: true
      },
      chartLabels: {
        type: Array,
        required: true
      },
      chartType: {
        type: String,
        default: 'line'
      },
      width: {
        type: String,
        default: '100%'
      },
      height: {
        type: String,
        default: '400px'
      }
    },
    mounted() {
      this.renderChart();
    },
    methods: {
      renderChart() {
        const ctx = this.$refs.chart.getContext('2d');
        new Chart(ctx, {
          type: this.chartType,
          data: {
            labels: this.chartLabels,
            datasets: [this.chartData]
          },
          options: {
            scales: {
              y: {
                beginAtZero: true
              }
            }
          }
        })
      }
    }
  };
  </script>
  