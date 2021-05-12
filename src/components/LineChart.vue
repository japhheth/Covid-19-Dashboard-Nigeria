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
  },
  mounted() {
    const states = this.chartData.map((item) => item.state);
    const total = this.chartData.map((item) => item.total);

    this.renderChart(
      {
        labels: states,
        datasets: [
          {
            label: this.label,
            data: total,
          },
        ]
      },
      this.options
    );
  },
};
</script>