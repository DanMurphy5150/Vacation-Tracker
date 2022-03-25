<template>
  <h1>Your Planned Vacations</h1>

  <div class="home">
    <PlanView v-if="inEditMode" title="Edit" :vacation="vacationToEdit" />
    <PlannedVacations
      v-else
      :vacations="vacations"
      @edit-vacation="editVacation"
      @delete-vacation="deleteVacation"
    ></PlannedVacations>
  </div>
</template>

<script>
import PlannedVacations from "../components/PlannedVacations.vue";
import PlanView from "./PlanView.vue";

import axios from "axios";
// @ is an alias to /src

const baseURL = "http://localhost:5000/vacations/";

export default {
  name: "HomeView",
  components: { PlannedVacations, PlanView },
  data() {
    return {
      vacations: [],
      inEditMode: false,
      vacationToEdit: [],
    };
  },
  methods: {
    async fetchVacations() {
      try {
        const res = await axios.get(baseURL);
        return res.data;
      } catch (err) {
        console.log(err);
      }
    },
    async deleteVacation(id) {
      const res = await axios.delete(baseURL + `${id}`);
      res.status === 200
        ? (this.vacations = this.vacations.filter(
            (vacation) => vacation.id !== id
          ))
        : alert("error while deleting vacation");
    },
    async editVacation(id) {
      const res = await axios.get(baseURL + `${id}`);
      const payload = res.data;
      this.vacationToEdit = [...this.vacationToEdit, payload];
      this.inEditMode = !this.inEditMode;
    },
  },
  async created() {
    this.vacations = await this.fetchVacations();
  },
};
</script>
