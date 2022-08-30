<template>
    <div  class="container">
      <Bar :chart-options="chartOptions" :chart-data="chartData" :chart-id="chartId" :dataset-id-key="datasetIdKey"
        :plugins="plugins" :css-classes="cssClasses" :styles="styles" :width="width" :height="height" />
      
    </div>
  </template>
  
  <script>
  import { Bar } from 'vue-chartjs'
  import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
  
  ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
  
  export default {
  
    name: 'BarChart',
    components: { Bar },
    props: {
      dateFim: String,
      dateInicio: String,
      quantiaDois: String,
      
      chartId: {
        type: String,
        default: 'bar-chart'
      },
      datasetIdKey: {
        type: String,
        default: 'label'
      },
      width: {
        type: Number,
        default: 200
      },
      height: {
        type: Number,
        default: 200
      },
      cssClasses: {
        default: '',
        type: String
      },
      styles: {
        type: Object,
        default: () => { 
          
        }
      },
      plugins: {
        type: Object,
        default: () => { }
      }
    },
  
    data() {
      return {
        chartData: {
          labels: ["dia - 01","jdia - 02", "dia - 03", "dia - 04"],
          datasets: [
            {
              label: 'Data One',
              backgroundColor: '#f87979',
              data: [5.02,3.29,5.15,1.98],
            }
          ]
        },
        dados:this.quantiaDois,
      }
    },
    
  }
  
  </script>

  <style scoped>

    .container{
      max-width: 500px;
    }

  </style>