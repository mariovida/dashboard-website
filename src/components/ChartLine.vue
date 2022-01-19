<template>
  <div class="example">
    <apexcharts class="pie" type="area" :options="chartOptions" :series="series"></apexcharts>
  </div>
</template>

<script>
import VueApexCharts from 'vue-apexcharts'

export default {
  name: 'Chart',
  components: {
    apexcharts: VueApexCharts,
  },
  data: function() {
    return {
      chartOptions: {
        legend: {
          show: false
        },
        chart: {
          type: 'area',
          zoom: {
            enabled: false
          },
          toolbar: {
            show: false
          }
        },
        dataLabels: {
          enabled: false
        },
        stroke: {
          curve: 'smooth'
        },
        xaxis: {
          type: 'datetime',
          categories: ["2022-01-13", "2022-01-14", "2022-01-15", "2022-01-16", "2022-01-17", "2022-01-18", "2022-01-19"]
        },
        tooltip: {
          x: {
            format: 'dd/MM/yy'
          },
        },
      },
      series: [{
        name: '2021',
        data: [31, 40, 28, 51, 42, 109, 100]
      }, {
        name: '2022',
        data: [11, 32, 45, 32, 34, 52, 41]
      }],
    }
  },
}
</script>

<style scoped>
</style>
