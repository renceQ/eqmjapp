<template>
    <userheader />
    <cancel />

  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import cancel from '@/components/user/cancel'
  
  export default defineComponent({
      components:{
          userheader,
          cancel,
      },
      created(){
          console.log(userheader);
          console.log(cancel);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  