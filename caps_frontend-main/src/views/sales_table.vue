<template>
    <div id="app">
      <Menu />
      <sales /><br><br><br>
      <AlertDefault :visible="false" variant="success" ></AlertDefault>

    </div>
  
  </template>
  
  <script>
  import Menu from '../components/admin/Menu.vue'
  import sales from '../components/admin/sales.vue'


  
  export default {
    name: "app",
    components: {
      Menu,
      sales,
    },
}
   </script>
   <style>

  </style>
  