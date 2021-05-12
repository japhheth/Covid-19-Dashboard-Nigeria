<template>
  <div id="app">
    <covid-stats
      :casesOnAdmission="casesOnAdmission"
      :confirmedCases="confirmedCases"
      :death="death"
      :discharged="discharged"
    />
  </div>
</template>

<script>
import CovidStats from "./components/covid-stats.vue";
import axios from "axios";
export default {
  name: "App",
  components: {
    CovidStats,
  },
  data: () => ({
    baseUrl: "https://covidnigeria.herokuapp.com/api",
    casesOnAdmission: [],
    confirmedCases: [],
    death: [],
    discharged: [],
  }),
  async created() {
    await axios
      .get(`${this.baseUrl}`)
      .then((response) => {
        const { states } = response.data.data;
        states.forEach((items) => {
          const {
            casesOnAdmission,
            confirmedCases,
            discharged,
            death,
            state,
          } = items;
          this.casesOnAdmission.push({ total: casesOnAdmission, state });
          this.confirmedCases.push({ total: confirmedCases, state });
          this.death.push({ total: death, state });
          this.discharged.push({ total: discharged, state });
        });
      })
      .catch((err) => console.log(err));
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
