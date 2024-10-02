<template>
    <userheader />
    <userhome />
  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import userhome from '../components/user/userhome.vue'
  
  export default defineComponent({
      components:{
          userheader,
          userhome,
      },
      created(){
          console.log(userheader);
          console.log(userhome);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  