<script>
/* eslint-disable vue/require-prop-types */
import { Doughnut } from 'vue-chartjs'
export default {
  extends: Doughnut,
  props: ['chartData', 'options'],
  mounted() {
    this.renderChart(this.chartData, this.options)
  },
}
</script>
