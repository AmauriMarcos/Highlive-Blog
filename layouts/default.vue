<template>
   <div>
      <MobileNavbar></MobileNavbar>
      <TheNavbar></TheNavbar>
      <nuxt></nuxt>
      <Footer></Footer>
   </div>
</template>

<script>
import Footer from "../components/Footer";
import TheNavbar from "../components/TheNavbar";
import MobileNavbar from "../components/MobileNavbar";
export default {
  components: {
     TheNavbar,
     MobileNavbar,
     Footer
  },
  
}
</script>
