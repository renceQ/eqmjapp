<template>
    <userheader />
    <cart />

  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import cart from '@/components/user/cart'
  
  export default defineComponent({
      components:{
          userheader,
          cart,
      },
      created(){
          console.log(userheader);
          console.log(cart);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  