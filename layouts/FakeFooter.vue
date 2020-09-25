<template>
   <div>
      <MobileNavbar></MobileNavbar>
      <TheNavbar></TheNavbar>
      <nuxt></nuxt>
     
   </div>
</template>

<script>

import TheNavbar from "../components/TheNavbar";
import MobileNavbar from "../components/MobileNavbar";
export default {
  components: {
     TheNavbar,
     MobileNavbar,
  
  },
  
}
</script>
