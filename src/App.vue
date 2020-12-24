<template>
  <div id="app" class="small-container">
    <h1>Employees</h1>
    <employee-table v-bind:employees="employees"/>
  </div>
</template>

<script>
import EmployeeTable from '@/components/EmployeeTable.vue'

export default {
  name: 'App',
  components: {
    EmployeeTable
  },
  data() {
    return {
      employees: [
        {
          id: 1,
          name: 'Reza',
          email: 'reza@mail.com'
        },
        {
          id: 2,
          name: 'Luky',
          email: 'luky@mail.com'
        }
      ]
    }
  }
}
</script>

<style>
  button {
    background: #009435;
    border: 1px solid #009435;
  }

  .small-container {
    max-width: 680px;
  }
</style>
