<template>
    <userheader_landing />
    <landing_page />
  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader_landing from '@/components/user/userheader_landing'
  import landing_page from '@/components/user/landing_page'
  
  export default defineComponent({
      components:{
          userheader_landing,
          landing_page,
      },
      created(){
          console.log(userheader_landing);
          console.log(landing_page);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  