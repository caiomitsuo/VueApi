<template>
  <div>
    <h1>Lista de Funcionarios</h1>
    <table class="table__funcionarios">
      <tr>
        <td>Nome</td>
        <td>Salario</td>
        <td>Idade</td>
      </tr>
      <tr v-for="item in list" v-bind:key="item.id">
        <td>{{ item.employee_name }}</td>
        <td>{{ item.employee_salary }}</td>
        <td>{{ item.employee_age }}</td>
      </tr>
    </table>
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
<style>
.table__funcionarios,td {
  border: 1px solid black;
}
</style>
