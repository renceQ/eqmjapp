<template>
    <userheader />
    <completed />

  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import completed from '@/components/user/completed'
  
  export default defineComponent({
      components:{
          userheader,
          completed,
      },
      created(){
          console.log(userheader);
          console.log(completed);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  