<template>
  <div id="app">
    <h1>Employees</h1>
    <employee-form @add:employee="addEmployee" />
    <employee-table :employees="employees" @delete:employeeId="deleteEmployee"/>
  </div>
</template>

<script>
import EmployeeTable from '@/components/EmployeeTable.vue'
import EmployeeForm from '@/components/EmployeeForm.vue'
export default {
  name: 'app',
  components: {
    EmployeeTable,
    EmployeeForm
  },
  data() {
    return {
      employees: [
        {
          id: 1,
          name: 'Richard Hendricks',
          email: 'richard@piedpiper.com',
        },
        {
          id: 2,
          name: 'Bertram Gilfoyle',
          email: 'gilfoyle@piedpiper.com',
        },
        {
          id: 3,
          name: 'Dinesh Chugtai',
          email: 'dinesh@piedpiper.com',
        }
      ]
    }
  },
  methods: {
    addEmployee(employee) {
      const lastId = 
      this.employees.length > 0 ? this.employees[this.employees.length - 1].id : 0;
      const id = lastId + 1;
      const newEmployee = { ...employee, id };

      this.employees = [...this.employees, newEmployee];
    },
    deleteEmployee(employeeId) {
      console.log("Delete an employee with ID:"+employeeId);
      this.employees = this.employees.filter(
      employee => employee.id !== employeeId
      )
    }
  }
}
</script>

<style>
   body {
    width: 60%;
    margin: auto;
  }
  button {
    background: #009435;
    border: 1px solid #009435;
  }
  .small-container {
    max-width: 680px;
  }
</style>
