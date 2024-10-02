<template>
    <userheader />
    <orderhistories />

  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import orderhistories from '@/components/user/orderhistories'
  
  export default defineComponent({
      components:{
          userheader,
          orderhistories,
      },
      created(){
          console.log(userheader);
          console.log(orderhistories);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  