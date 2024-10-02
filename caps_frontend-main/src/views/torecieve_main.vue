<template>
    <userheader />
    <torecieve />

  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import torecieve from '@/components/user/torecieve'
  
  export default defineComponent({
      components:{
          userheader,
          torecieve,
      },
      created(){
          console.log(userheader);
          console.log(torecieve);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  