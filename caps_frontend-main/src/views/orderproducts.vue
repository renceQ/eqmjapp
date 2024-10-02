<template>
    <div id="app">
      <Menu />
      <orderproducts_list /><br><br><br>
      <AlertDefault :visible="false" variant="success" ></AlertDefault>

    </div>
  
  </template>
  
  <script>
  import Menu from '../components/admin/Menu.vue'
  import orderproducts_list from '../components/admin/orderproducts_list.vue'


  
  export default {
    name: "app",
    components: {
      Menu,
      orderproducts_list,
    },
}
   </script>
   <style>

  </style>
  