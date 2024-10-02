<template>
    <productrequestfields />  
  </template>
    
  <script>
  import axios from 'axios'
  import { defineComponent } from 'vue';
  import productrequestfields from '@/components/user/productrequestfields'
  
  export default defineComponent({
      components:{
          productrequestfields,
      },
      created(){
          console.log(productrequestfields);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  