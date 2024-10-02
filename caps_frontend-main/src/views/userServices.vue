<template>
    <userheader />
    <userServ />
  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import userServ from '../components/user/userServ.vue'
  
  export default defineComponent({
      components:{
          userheader,
          userServ,
      },
      created(){
          console.log(userheader);
          console.log(userServ);
      }
  });
  </script>
  
  <style>
  
  </style>
  