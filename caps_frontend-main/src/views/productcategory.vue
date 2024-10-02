<template>
    <div id="app">
      <Menu />
      <category /><br><br><br>
      <AlertDefault :visible="false" variant="success" ></AlertDefault>

    </div>
  
  </template>
  
  <script>
  import Menu from '../components/admin/Menu.vue'
  import category from '../components/admin/category.vue'


  
  export default {
    name: "app",
    components: {
      Menu,
      category,
    },
}
   </script>
   <style>

  </style>
  