<template>
    <userheader />
<usercontactus />
  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
  import usercontactus from '@/components/user/usercontactus'

  
  export default defineComponent({
      components:{
          userheader,
          usercontactus,

      },
      created(){
          console.log(userheader);
          console.log(usercontactus);

      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  