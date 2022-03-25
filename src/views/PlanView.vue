<template>
  <h1>{{ title }} Your Vacation</h1>

  <PlanningVacationForm
    @edit-vacation-payload="$emit('edit-vacation-payload', vacation)"
  />
</template>

<script>
import PlanningVacationForm from "../components/PlanningVacationForm.vue";

export default {
  name: "PlanView",
  props: {
    title: {
      type: String,
      default: "Plan",
    },
    vacation: {
      type: Object,
    },
  },

  components: {
    PlanningVacationForm,
  },
};
</script>
