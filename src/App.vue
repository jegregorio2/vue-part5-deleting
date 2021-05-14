<template>
  <div id="app" class="container-sm">
    <h1>Employees</h1>
    <employee-form @add:employee="addEmployee" />
    <!-- add @delete -->
    <employee-table :employees="employees"
    @delete:employee="deleteEmployee" />
  </div>
</template>

<script>
  import EmployeeTable from '@/components/EmployeeTable.vue'
  import EmployeeForm from '@/components/EmployeeForm.vue'
  
  export default {
    name: 'App',
    components: {
      EmployeeTable,
      EmployeeForm,
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
          },
        ],
      }
    },
    methods: {
      addEmployee(employee) {
        // this.employees = [...this.employees, employee]
        // this one stuck, it does not move to the next one
        const lastId =
          this.employees.length > 0
            ? this.employees[this.employees.length - 1].id
            : 0;
        const id = lastId + 1;
        const newEmployee = { ...employee, id };
        this.employees = [...this.employees, newEmployee];
        // this one, you can keep add more employees
      },
      // add delete employee
      deleteEmployee(id) {
        this.employees = this.employees.filter(employee => employee.id !== id)
      },
    },
  }
</script>

<style scoped>
  button {
  background: #009435;
    border: 1px solid #009435;
  }
  .container-sm {
    max-width: 680px;
  } 
</style>
