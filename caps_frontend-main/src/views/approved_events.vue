<template>
    <Menu />
<approvedevents />
  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import Menu from '@/components/admin/Menu.vue'
  import approvedevents from '../components/admin/approvedevents.vue'

  
  export default defineComponent({
      components:{
          Menu,
          approvedevents,

      },
      created(){
          console.log(Menu);
          console.log(approvedevents);

      }
  });
  </script>
  
  <style>
  
  </style>
  
  
  