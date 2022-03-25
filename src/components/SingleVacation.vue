<template>
  <div class="vacation-card">
    <h2>
      {{ singleVacation.location }} Vacation
      <span>
        <i
          class="fas fa-pen edit-icon"
          @click="$emit('edit-vacation', singleVacation.id)"
        ></i
        ><i
          class="fas fa-times delete-icon"
          @click="$emit('delete-vacation', singleVacation.id)"
        ></i>
      </span>
    </h2>

    <ul>
      <li>Start Date: {{ singleVacation.startDate }}</li>
      <li>End Date: {{ singleVacation.endDate }}</li>
    </ul>
    <div @click="expandVacationInfo">
      <i
        :class="
          vacationInfoExpanded
            ? 'fas fa-arrow-up expand-icon'
            : 'fas fa-arrow-down expand-icon'
        "
      ></i>

      <ul v-if="vacationInfoExpanded">
        <li>Estimated Cost: {{ singleVacation.estimatedCost }}</li>
        <li>Amount Saved: {{ singleVacation.savedAmount }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "SingleVacation",
  props: {
    singleVacation: {
      id: {
        type: Number,
        required: true,
      },
      location: {
        type: String,
        required: true,
      },
      startDate: {
        type: String,
      },
      endDate: {
        type: String,
      },
      estimatedCost: {
        type: Number,
      },
      savedAmount: {
        type: Number,
      },
    },
  },
  data() {
    return {
      vacationInfoExpanded: false,
    };
  },
  methods: {
    expandVacationInfo() {
      // grab the id
      // display the cost info if the arrow is expanded
      //on expansion arrow should change to up arrow
      console.log("Click");
      this.vacationInfoExpanded = !this.vacationInfoExpanded;
      console.log(this.vacationInfoExpanded);
    },
    // editVacation() {
    //   console.log("edit mode");
    // },
    // deleteVacation() {
    //   alert("Are you sure you want to delete your Planned Vacation?");
    // },
  },
};
</script>

<style scoped>
.delete-icon {
  color: black;
  font-size: 1rem;
}

.edit-icon {
  color: #020202;
  padding-right: 25px;
  font-size: 1rem;
}

.expand-icon {
  color: #070707;
  font-size: 17px;
  margin-top: 2%;
}
.vacation-card {
  background: #717b72;
  margin: 3%;
  padding: 7px 20px 0px 10px;
  cursor: pointer;
  box-shadow: 6px 3px 3px #090a0b;
  width: 95%;
  border-radius: 10px;
}
.vacation-card:hover {
  box-shadow: 6px 5px 5px #79a2cb;
}

.vacation-card h2 {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 1%;
  border-bottom: 4px solid rgb(194, 166, 131);
  color: #070707;
}
.vacation-card ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
.vacation-card li {
  display: inline-block;
  border-radius: 10px;
  margin: 0px 10px 0px 10px;
  padding: 1rem;
  color: black;
}
</style>
