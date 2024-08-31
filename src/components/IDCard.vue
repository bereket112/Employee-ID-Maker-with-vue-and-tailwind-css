<template>
  <div class="sm: flex flex-col overflow-none  shadow-emerald-950">
     <div>
      
    
  <div :class="['p-4 rounded-lg shadow-lg relative flex items-center', roleClass]">

    
    <button @click="deleteCard" class="absolute top-0 right-0 bg-red-500 w-6 text-white p-1 rounded-sm hover:bg-red-700 hover:text-balance">X</button>
    
    <img :src="image" alt="Employee Image" class="w-24  rounded-sm h-full border-[1px] border-yellow-500 shadow-md mr-[7px]">
    <div >
      
      <h2 class="text-gray-700font-bold flex flex-row"><p class="  mr-2 font-sans text-sm ">Full Name:</p>{{ name }}</h2>
      <h2 class="text-gray-700 flex flex-row"><p class="  mr-2 font-sans text-sm "> phone:</p>{{ phone }}</h2>
      <div class="mt-4p-2 rounded-lg shadow-inner">
        <h2 class="text-gray-700 flex flex-row "><p class="  mr-2 font-sans text-sm ">company Name:</p>{{ companyName }}</h2>
        <!-- <p class="font-semibold"> possition: {{ roles }}</p> -->
        <h2 class="text-sm text-gray-600 flex flex-row "><p class="  mr-2 font-sans text-sm ">company address:</p>{{ address }}</h2>
        <!-- <div class="flex space-x-4 mt-2  bg-white ">
          <img v-for="link in socialLinks" :key="link.name" :src="link.image" :alt="link.name" class="w-6 h-6">
        </div> -->
      </div>
    </div>
  </div>
    </div>
  </div> 
</template>

<script>
export default {
  props: {
    name: String,
    phone: String,
    image: String,
    role: String,
    companyName: String,
    address: String,
    socialLinks: Array
  },
  methods: {
    deleteCard() {
      this.$emit('delete-card', this.name);
    }
  },
  computed: {
    roleClass() {
      switch (this.role) {
        case 'Manager':
          return 'bg-emerald-300 border-2 border-black';
        case 'Developer':
          return 'bg-sky-200';
        case 'Designer':
          return 'bg-red-200';
        default:
          return 'bg-gray-200';
      }
    
    
    }
    
  }
  // computed:{
  //   roles(){
  //     if (this.role)={'Manager' {
  //     case'Manager' , 'bg-emerald-300 border-2 border-black':
  //     return 'Manager';
  //     case'Developer':
  //     return 'Developer';
  //       case'Designer':
  //     return 'Designer';

  //     }
  //   }
  // }

}
</script>
