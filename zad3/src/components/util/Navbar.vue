<template>
  <mdb-navbar dark color="deep-purple accent-4" >
    <mdb-navbar-brand class="text-white">{{msg}}</mdb-navbar-brand>
  </mdb-navbar>
</template>

<script>
  import {
    mdbNavbar,
    mdbNavbarBrand,
  } from 'mdbvue';

  export default {
    name: "Navbar",

    components: {
      mdbNavbar,
      mdbNavbarBrand,
    },

    props: {
      msg: String
    },

  }
</script>

<style scoped>

</style>