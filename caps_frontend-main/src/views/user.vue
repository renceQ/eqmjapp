<template>
  <userheader />
</template>
  
<script>
import { defineComponent } from 'vue';
import userheader from '@/components/user/userheader'

export default defineComponent({
    components:{
        userheader,
    },
    created(){
        console.log(userheader);
    }
});
</script>

<style>

</style>


