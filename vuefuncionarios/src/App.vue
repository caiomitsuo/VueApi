<template>
  <div id="app">
    <EmployeeList />
    <BitApi />
  </div>
</template>

<script>
import EmployeeList from "./components/EmployeeList";
import BitApi from "./components/BitApi";
export default {
  name: "App",
  components: {
    EmployeeList,
    BitApi,
  },
};
</script>

<style>

</style>
