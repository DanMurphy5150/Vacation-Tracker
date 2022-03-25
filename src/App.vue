<template>
  <div class="nav-container">
    <Header title="Vacation Planner" />
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link
        @edit-vacation-payload="receiveEditVacationPayload"
        to="/plan"
        >Plan a Vacation</router-link
      >
      |
      <router-link to="/about">About</router-link>
      <router-link to="/edit"></router-link>
    </nav>
  </div>
  <div class="container">
    <router-view />
  </div>
</template>

<script>
import Header from "./components/Header.vue";

export default {
  components: {
    Header,
  },
  data() {
    return {
      editVacationPayload: [],
    };
  },
  methods: {
    receiveEditVacationPayload(payload) {
      this.editVacationPayload = [...this.editVacationPayload, payload];
      console.log(this.editVacationPayload);
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: "Jost", sans-serif;
}

body {
  margin: 0;
}

h1 {
  color: rgb(194, 166, 131) !important;
}

/* * {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
} */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #6a8787;
}

:root {
  background-color: #636c6e;
}

nav {
  padding: 5px;
}

nav a {
  font-weight: bold;
  color: #3282b8;
}

nav a.router-link-exact-active {
  color: #bbe1fa;
}

.nav-container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 150px;
  border: 1px solid #0f4c75;
  padding: 30px;
  border-radius: 5px;
  background-color: #11201e;
  box-shadow: 5px 5px 8px rgba(0, 0, 0, 0.947);
}
.container {
  max-width: 80%;
  min-width: 70%;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid #0f4c75;
  padding: 30px;
  border-radius: 5px;
  background-color: #11201e;
  box-shadow: 5px 5px 8px rgba(0, 0, 0, 0.92);
}
/* .btn {
  display: inline-block;
  background: #00070b;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  width: 90%;
} */
</style>
