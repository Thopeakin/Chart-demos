<template>
  <div id="app">
    <Charts/>
  </div>
</template>

<script>
import Charts from './components/charts.vue'

export default {
  name: 'App',
  components: {
    Charts
  }
}
</script>

<style>
*{
  padding: 0;
  margin: 0;
  background-color: #EDF;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 30px;
}
</style>
