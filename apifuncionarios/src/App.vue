<template>
  <div id="app">
    <h1>LISTA</h1>
    <EmployeeList />
  </div>
</template>
<script>
import EmployeeList from "./components/EmployeeList";
export default {
  name: "App",
  components: {
    EmployeeList,
  },
};
</script>
<style></style>
