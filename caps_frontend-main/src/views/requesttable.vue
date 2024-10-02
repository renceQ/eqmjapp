<template>
    <div id="app">
      <Menu />
      <requestTable />
    </div>
  
  </template>
  
  <script>
  import Menu from '../components/admin/Menu.vue'
  import requestTable from '../components/admin/requestTable.vue'
  
  export default {
    name: "app",
    components: {
      Menu,
      requestTable,
    },
}
   </script>
   <style>

  </style>
  