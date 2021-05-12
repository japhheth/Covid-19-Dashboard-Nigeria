<script>
import { Line } from "vue-chartjs";
export default {
  extends: Line,
  props: {
    label: {
      type: String,
    },
    chartData: {
      type: Array,
    },
    options: {
      type: Object,
    },
    chartColors: {
        type: Object
    }
  },
  mounted() {
    const states = this.chartData.map((item) => item.state);
    const total = this.chartData.map((item) => item.total);
    console.log(this.chartColors, 'checking')
    const {borderColor, pointBorderColor, pointBackgroundColor, backgroundColor} = this.chartColors
    this.renderChart(
      {
        labels: states,
        datasets: [
          {
            label: this.label,
            data: total,
            borderColor: borderColor,
            pointBorderColor: pointBorderColor,
            pointBackgroundColor: pointBackgroundColor,
            backgroundColor: backgroundColor
          },
        ]
      },
      this.options
    );
  },
};
</script>