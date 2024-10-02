<template>
    <userheader />
<userbookevents />
  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import userbookevents from '../components/user/userbookevents.vue'

  
  export default defineComponent({
      components:{
          userheader,
          userbookevents,

      },
      created(){
          console.log(userheader);
          console.log(userbookevents);

      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  