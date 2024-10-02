<template>
    <userheader />
    <userprod />
  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import userprod from '@/components/user/userprod'
  
  export default defineComponent({
      components:{
          userheader,
          userprod
      },
      created(){
          console.log(userheader);
          console.log(userprod);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  