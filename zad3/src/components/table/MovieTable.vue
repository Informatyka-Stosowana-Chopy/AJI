<template>
  <div class="table_movies"> 
    <table class="table table-striped table-bordered mb-0">
      <thead class="white-text deep-purple">
        <tr class="text-center">
          <th>Title</th>
          <th>Production Year</th>
          <th>Cast</th>
          <th>Genres</th>
        </tr>
      </thead>
      <tbody>
        <!--INDEX IS ONLY BECAUSE FIRST VALUE RECEIVES COUNTING
        FROM 1 AND SECOND VALUE IS COUNTED FROM 0-->
        <tr class="text-center" v-for="(index,it) in tableSize" :key="it">
          <th>{{jsonData[it].title}}</th>
          <th>{{jsonData[it].year}}</th>
          <th>{{jsonData[it].cast.toString().split(",").join("\n")}}</th>
          <th>{{jsonData[it].genres.toString().split(",").join("\n")}}</th>
        </tr>
      </tbody>
    </table>

    <div v-if="isButtonVisible">
      <button class="btn btn-block deep-purple lighten-1 white-text m-0" v-on:click="expandTable()">
        Load Next
      </button>
    </div>
  </div>
</template>

<script>
  const INITIAL_TABLE_SIZE = 10;

  export default {
    name: "MovieTable",

    props: {
      jsonData: Array,
    },

    data() {
      let tableSize = INITIAL_TABLE_SIZE;
      let isButtonVisible = true;

      if (this.jsonData.length < INITIAL_TABLE_SIZE) {
        tableSize = this.jsonData.length;
        isButtonVisible = false;
      } else {
        tableSize = INITIAL_TABLE_SIZE;
        isButtonVisible = true;
      }

      return {
        tableSize,
        isButtonVisible
      }
    },

    methods: {
      expandTable: function () {
        if (this.jsonData.length + INITIAL_TABLE_SIZE <= this.tableSize) {
          this.tableSize = this.jsonData.length;
          this.isButtonVisible = false;
        } else {
          this.tableSize += INITIAL_TABLE_SIZE;
          this.isButtonVisible = true;
        }
      }
    },

  }
</script>

<style scoped>
  th {
    padding: 0.5rem !important;
  }

  .table_movies {
    margin: 0 auto;
  }
</style>
