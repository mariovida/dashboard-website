<template>
  <div class="example">
    <apexcharts class="pie" :options="chartOptions" :series="series"></apexcharts>
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
        labels: ["Food", "Bills", "Home", "Gas"],
        chart: {
          type: 'donut'
        },
        legend: {
          position: "right",
        },
        dataLabels: {
          enabled: true
        },
        responsive: [
        {
          breakpoint: 768,
          options: {
            legend: {
              position: "left"
            }
          }
        }
      ]
      },
      series: [267, 512, 760, 180]
    }
  },
}
</script>

<style scoped>
</style>
