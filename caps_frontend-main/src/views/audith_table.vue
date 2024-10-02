<template>
    <div id="app">
      <Menu />
      <audith /><br><br><br>
      <AlertDefault :visible="false" variant="success" ></AlertDefault>

    </div>
  
  </template>
  
  <script>
  import Menu from '../components/admin/Menu.vue'
  import audith from '../components/admin/audith.vue'


  
  export default {
    name: "app",
    components: {
      Menu,
      audith,
    },
}
   </script>
   <style>

  </style>
  