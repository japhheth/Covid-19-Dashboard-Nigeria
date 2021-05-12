<template>
  <div class="container">
      hello
  </div>
</template>

<script>
import LineChart from "./LineChart";
export default {
  components: {
    LineChart
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
};
</script>

<style>
</style>