<template>
    <div id="app">
      <Menu />
      <prodtable /><br><br><br>

    </div>
  
  </template>
  
  <script>
  import Menu from '../components/admin/Menu.vue'
  import prodtable from '../components/admin/prodtable.vue'
 
  
  export default {
    name: "app",
    components: {
      Menu,
      prodtable,

    },
}
   </script>
   <style>

  </style>
  