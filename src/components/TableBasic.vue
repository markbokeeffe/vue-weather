<template>
  <div>
    <md-table>
      <md-table-row>
        <md-table-head v-for="column in this.table.columns" :key="column" >{{ column }}</md-table-head>
      </md-table-row>

      <md-table-row>
        <md-table-cell v-for="row in this.table.rows" :key="row">{{ row }}</md-table-cell>
      </md-table-row>
    </md-table>
  </div>
</template>

<script>
  export default {
    name: 'TableBasic',
    props: {
      table: Object
    }
  }
</script>

<style scoped>
  .md-table-cell {
    text-align: left
  }
  .md-table-head {
    background-color:#8080fd;
    color: #fff;
    font-weight: bold;
    font-size: 15px;
  }
  .md-table-cell {
    background-color: #fff;
  }
</style>