<template>
    <userheader />
    <pending />

  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import pending from '@/components/user/pending'
  
  export default defineComponent({
      components:{
          userheader,
          pending,
      },
      created(){
          console.log(userheader);
          console.log(pending);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  