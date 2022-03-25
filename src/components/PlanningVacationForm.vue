<template>
  <form class="add-form" @edit-vacation-payload="recievePayload">
    <div class="form-control">
      <label>Location</label>
      <input
        type="text"
        v-model="location"
        name="location"
        placeholder="Where are you Going on Vacation?"
      />
    </div>
    <div class="form-control">
      <label for="">When does your vacation start?</label>
      <input
        type="text"
        v-model="startDate"
        name="startDate"
        placeholder="Start date: DD/MM/YYYY"
      />
    </div>
    <div class="form-control">
      <label for="">When does your vacation end?</label>
      <input
        type="text"
        v-model="endDate"
        name="endDate"
        placeholder="End date: DD/MM/YYYY"
      />
    </div>
    <div class="form-control">
      <label for="">What is the estimated cost?</label>
      <input
        type="text"
        v-model="estimatedCost"
        name="estimatedCost"
        placeholder="Estimated cost: XXXX.XX USD"
      />
    </div>
    <div class="form-control">
      <label for="">How much have you already saved for this trip?</label>
      <input
        type="text"
        v-model="savedAmount"
        name="savedAmount"
        placeholder="Saved amount: XXXX.XX USD"
      />
    </div>

    <input
      type="submit"
      values="Save Vacation"
      class="btn btn-block"
      @click="createVacation"
    />
  </form>
</template>

<script>
import axios from "axios";

const baseURL = "http://localhost:5000/vacations";

export default {
  name: "PlanningVacationForm",
  data() {
    return {
      location: "",
      startDate: "",
      endDate: "",
      estimatedCost: "",
      savedAmount: "",
      editPayload: [],
    };
  },
  methods: {
    async createVacation(event) {
      event.preventDefault();

      if (!this.location) {
        alert("Please add a location for your Vacation planning");
        return;
      }
      const newVacation = {
        // id: Math.floor(Math.random() * 100000),
        location: this.location,
        startDate: this.startDate,
        endDate: this.endDate,
        estimatedCost: this.estimatedCost,
        savedAmount: this.savedAmount,
      };

      await axios.post(baseURL, newVacation);

      // this.$emit("add-vacation", newVacation);

      this.location = "";
      this.startDate = "";
      this.endDate = "";
      this.estimatedCost = "";
      this.savedAmount = "";
    },
    recievePayload(vacation) {
      this.editPayload = [...this.editPayload, vacation];
      console.log(this.editPayload);
    },
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px 0;
}

.form-control label {
  font-weight: bold;
  margin-right: 1rem;
  width: 7rem;
  display: inlne-block;
  text-align: left;
  padding-left: 22px;
}

.form-control input {
  width: 90%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
  box-shadow: 2px 2px 5px #bbe1fa;
  background-color: rgba(233, 226, 226, 0.803);
}

/* .form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
} */

/* .form-control-check label {
  flex: 1;
}

.form-control-check input {
  flex: 2;
  height: 20px;
} */
</style>
