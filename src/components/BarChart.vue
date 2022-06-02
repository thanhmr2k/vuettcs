<template>
  <Bar 
    :chart-options="chartOptions"
    :chart-data="chartData"
    :chart-id="chartId"
    :dataset-id-key="datasetIdKey"
    :plugins="plugins"
    :css-classes="cssClasses"
    :styles="styles"
    :width="width"
    :height="height"   
  />
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarChart',
  components: { Bar },
  props: {
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
      default: 450
    },
    height: {
      type: Number,
      default: 450
    },
    cssClasses: {
      default: '',
      type: String
    },
    styles: {
      type: Object,
      default: () => {}
    },
    plugins: {
      type: Object,
      default: () => {}
    },
  },

  data() {
    return {
      chartData: {
        labels: [ 'Monday',
        'Tuesday',
        'Wednesday',
        'Thursday',
        'Friday',
        'Saturday',
        'Sunday', ],
        datasets: [ { 
          label: 'Max temperature',
          backgroundColor: '#f87979',
          data: [34,34,37,36,30,31,32] 
          } ],

      },
      chartOptions: {
        responsive: false,
        maintainAspectRatio: true,
      }
    }
  },

}
</script>
<style scoped>
*{
  color: aliceblue;
   background-image: none !important;
}
</style>