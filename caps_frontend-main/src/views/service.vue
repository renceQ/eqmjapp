<template>
    <add_service />
  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import add_service from '@/components/admin/add_service.vue'
  
  export default defineComponent({
      components:{
          add_service,
      },
      created(){
          console.log(add_service);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  