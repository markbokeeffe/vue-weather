<template>
  <div id="app">
    <Report title="Weather Forecast"/>
  </div>
</template>

<script>
import Report from './components/Report.vue'

export default {
  name: 'app',
  components: {
    Report
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body{
    
}
</style>
