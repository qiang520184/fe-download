<template>
  <div id="app">
    <Download/>
  </div>
</template>

<script>
import Download from './components/Download.vue'
export default {
  name: 'app',
  components: {
    Download
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
  margin-top: 60px;
}
</style>
