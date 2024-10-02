<template>

    <userheader />
    <editprofile />

  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import userheader from '@/components/user/userheader'
import editprofile from '@/components/user/editprofile.vue';
  
  export default defineComponent({
      components:{
    userheader,
    editprofile,
},
      created(){
          console.log(editprofile);
          console.log(userheader);
      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  