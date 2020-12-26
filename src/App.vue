<template>
  <div id="app" class="small-container">
    <h1>Employees</h1>
    <employee-form 
      @add:employee="addEmployee"
      @edit:employee="editEmployee"
    />
    <employee-table 
      v-bind:employees="employees"
      @delete:employee="deleteEmployee"
    />
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
    },

    deleteEmployee(id) {
      this.employees = this.employees.filter( employee =>
        employee.id !== id
      )
    },

    editEmployee(updatedEmployee, id) {
      this.employees =this.employees.map( employee => 
        employee.id === id ? updatedEmployee : employee
      )
    },
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
