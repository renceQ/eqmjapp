<template>
    <userheader />
    <userblogs />
  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import userblogs from '@/components/user/userblogs'
  
  export default defineComponent({
      components:{
          userheader,
          userblogs,
      },
      created(){
          console.log(userheader);
          console.log(userblogs);
      }
  });
  </script>
  
  <style>
  
  </style>

  
  
  
  