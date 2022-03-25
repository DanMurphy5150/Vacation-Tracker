<template>
  <div :key="vacation.id" v-for="vacation in vacations">
    <SingleVacation
      :singleVacation="vacation"
      @edit-vacation="$emit('edit-vacation', vacation.id)"
      @delete-vacation="$emit('delete-vacation', vacation.id)"
    />
  </div>
</template>

<script>
import SingleVacation from "./SingleVacation.vue";

export default {
  name: "PlannedVacations",
  props: {
    vacations: {
      type: Array,
    },
  },
  components: {
    SingleVacation,
  },
  emits: ["edit-vacation", "delete-vacation"],
};
</script>
