<template>
    <div id="app">
      <Menu />
      <booking /><br><br><br>
      

    </div>
  
  </template>
  
  <script>
  import Menu from '../components/admin/Menu.vue'
  import booking from '../components/admin/booking.vue'


  
  export default {
    name: "app",
    components: {
      Menu,
      booking,
    },
}
   </script>
   <style>

  </style>
  