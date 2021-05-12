<template>
  <div class="container">
    <h1 class="text-center">COVID-19 Data Visualization in Nigeria</h1>
    <div class="row mt-5" v-if="casesOnAdmission.length > 0">
      <div class="col">
        <h4 class="text-left">Cases on admission</h4>
        <line-chart
          :chartData="casesOnAdmission"
          label="Cases on admission"
          :options="chartOptions"
          :chartColors="positiveChartColors"
        ></line-chart>
      </div>
    </div>
    <div class="row mt-5" v-if="confirmedCases.length > 0">
      <div class="col">
        <h4 class="text-left">Confirmed cases</h4>
        <line-chart
          :chartData="confirmedCases"
          label="Confirmed cases"
          :options="chartOptions"
          :chartColors="positiveChartColors"
        ></line-chart>
      </div>
    </div>
    <div class="row mt-5" v-if="death.length > 0">
      <div class="col">
        <h4 class="text-left">Death</h4>
        <line-chart
          :chartData="death"
          label="Death"
          :options="chartOptions"
          :chartColors="positiveChartColors"
        ></line-chart>
      </div>
    </div>
    <div class="row mt-5" v-if="discharged.length > 0">
      <div class="col">
        <h4 class="text-left">Discharged</h4>
        <line-chart
          :chartData="discharged"
          label="Discharged"
          :options="chartOptions"
          :chartColors="positiveChartColors"
        ></line-chart>
      </div>
    </div>
  </div>
</template>

<script>
import LineChart from "./LineChart";
export default {
  components: {
    LineChart,
  },
  data() {
    return {
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false,
      },
      positiveChartColors: {
        borderColor: "#077187",
        pointBorderColor: "#0E1428",
        pointBackgroundColor: "#AFD6AC",
        backgroundColor: "#74A57F",
      },
    };
  },
  props: {
    casesOnAdmission: {
      type: Array,
      required: true,
    },
    confirmedCases: {
      type: Array,
      required: true,
    },
    death: {
      type: Array,
      required: true,
    },
    discharged: {
      type: Array,
      required: true,
    },
  },
  mounted() {
    console.log(this.casesOnAdmission);
  },
};
</script>

<style>
</style>