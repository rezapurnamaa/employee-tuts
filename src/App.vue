<template>
  <div id="app" class="small-container">
    <h1>Employees</h1>
    <employee-form @add:employee="addEmployee"/>
    <employee-table v-bind:employees="employees"/>
  </div>
</template>

<script>
import EmployeeTable from '@/components/EmployeeTable'
import EmployeeForm from '@/components/EmployeeForm'
export default {
  name: 'App',
  components: {
    EmployeeTable,
    EmployeeForm
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
  },
  methods: {
    addEmployee(employee) {

      const lastId = this.employees.length > 0 
        ? this.employees[this.employees.length - 1].id 
        : 0
      const id = lastId + 1
      const newEmployee = {...employee, id}
      this.employees = [...this.employees, newEmployee]
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
