<template>
    <userheader />
    <toship />

  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import toship from '@/components/user/toship'
  
  export default defineComponent({
      components:{
          userheader,
          toship,
      },
      created(){
          console.log(userheader);
          console.log(toship);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  