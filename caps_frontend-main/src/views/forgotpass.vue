<template>
    <userforgotpass />
  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userforgotpass from '@/components/user/userforgotpass'
  
  export default defineComponent({
      components:{
          userforgotpass,
      },
      created(){
          console.log(userforgotpass);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  