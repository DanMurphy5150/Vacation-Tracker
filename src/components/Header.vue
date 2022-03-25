<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  name: "HeaderComponent",
  props: {
    title: {
      type: String,
      default: "Vacation Planner",
    },
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
  font-size: 1.5em;
}
</style>
