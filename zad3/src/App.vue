<template>
  <div id="app">
    <Navbar msg="Film Website"/>

    <div class="container-fluid">
      <Table :fullJsonData="fullMoviesData"/>
    </div>
  </div>
</template>

<script>
  import json from "./data/movies.json";
  import Navbar from "./components/util/Navbar";
  import Table from "./components/Table";

  export default {
    name: 'app',

    components: {
      Navbar,
      Table,
    },

    data() {
      return {
        fullMoviesData: json
      }
    },

  }
</script>

<style>
  * {
    margin: 0;
    padding: 0;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
</style>
