<template>
  <div class="container mx-auto p-4">
    <div class="flex justify-center space-x-4 mb-4">
      <button @click="showForm = true" class="bg-blue-500 text-white p-2 rounded hover:bg-blue-700">Create ID Card</button>
      <button @click="showForm = false" class="bg-green-500 text-white p-2 rounded hover:bg-green-700">View ID Cards</button>
    </div>
    <EmployeeForm v-if="showForm" @create-id="addEmployee" />
    <div v-else class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 mt-4">
      <IDCard v-for="employee in employees" :key="employee.name" v-bind="employee" @delete-card="deleteEmployee" />
    </div>
  </div>
</template>

<script>
import EmployeeForm from './components/EmployeeForm.vue'
import IDCard from './components/IDCard.vue'

export default {
  components: {
    EmployeeForm,
    IDCard
  },
  data() {
    return {
      employees: [],
      showForm: false // Start with the view mode
    }
  },
  methods: {
    addEmployee(employee) {
      this.employees.push(employee);
      this.showForm = false; // Switch to view mode after adding an employee
    },
    deleteEmployee(name) {
      this.employees = this.employees.filter(employee => employee.name !== name);
    }
  }
}
</script>
