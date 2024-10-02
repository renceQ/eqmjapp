<template>
    <userheader />
<userabout />
  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import userabout from '@/components/user/userabout'

  
  export default defineComponent({
      components:{
          userheader,
          userabout,

      },
      created(){
          console.log(userheader);
          console.log(userabout);

      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  