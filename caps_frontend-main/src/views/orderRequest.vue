<template>
    <div id="app">
      <Menu />
      <productrequest /><br><br><br>
      <AlertDefault :visible="false" variant="success" ></AlertDefault>

    </div>
  
  </template>
  
  <script>
  import Menu from '../components/admin/Menu.vue'
  import productrequest from '../components/admin/productrequest.vue'


  
  export default {
    name: "app",
    components: {
      Menu,
      productrequest,
    },
}
   </script>
   <style>

  </style>
  