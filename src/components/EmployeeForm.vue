<template>
    <form @submit.prevent="submitForm" class="flex flex-col  border-green-200 border-2 shadow-md rounded-md shadow-gray-200 w-56 m-2">
      <input v-model="name" required placeholder="Full Name" class="border-green-400  w-fit">
      <input v-model="phone" required placeholder="Phone" class="border p-2 mb-2 w-fit">
      <input v-model="image" required placeholder="Image URL" class="border p-2 mb-2 w-fit">
      <select v-model="role" required class="border p-2 mb-2 w-fit">
        <option value="Manager">Manager</option>
        <option value="Developer">Developer</option>
        <option value="Designer">Designer</option>
      </select>
      <input v-model="companyName" required placeholder="Company Name" class="border p-2 mb-2 w-fit">
      <input v-model="address" placeholder="Address" class="border p-2 mb-2 w-fit">
      <input v-model="socialLinks" placeholder="Social Media Links (comma separated)" class="border p-2 mb-2 w-full">
      <button type="submit" class="bg-blue-500 text-white p-2 rounded w-fit">Create ID</button>
    </form>
  </template>
  
  <script>
  export default {
    data() {
      return {
        name: '',
        phone: '',
        image: '',
        role: '',
        companyName: '',
        address: '',
        socialLinks: ''
      }
    },
    methods: {
      submitForm() {
        const links = this.socialLinks.split(',').map(link => ({ name: link.trim(), image: link.trim() }));
        this.$emit('create-id', { name: this.name, phone: this.phone, image: this.image, role: this.role, companyName: this.companyName, address: this.address, socialLinks: links });
      }
    }
  }
  </script>
  