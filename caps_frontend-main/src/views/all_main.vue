<template>
    <userheader />
    <all />

  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import all from '@/components/user/all'
  
  export default defineComponent({
      components:{
          userheader,
          all,
      },
      created(){
          console.log(userheader);
          console.log(all);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  