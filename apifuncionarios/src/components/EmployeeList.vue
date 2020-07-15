<template>
  <div class="list_funcionarios">
    <h1>EmployeeList</h1>
    <ul>
      <li v-for="item in list" v-bind:key="item.id">
        {{ item.employee_name }}
        {{ item.employee_salary }}
        {{ item.employee_age }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "EmployeeList",
  data() {
    return { list: undefined };
  },
  mounted() {
    axios
      .get("http://dummy.restapiexample.com/api/v1/employees")
      .then((resp) => {
        this.list = resp.data.data;
        console.warn(resp.data.data);
      });
  },
};
</script>
<style></style>
