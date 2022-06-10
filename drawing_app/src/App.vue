<template>
  <div id="app">
    <DrawingCanvas></DrawingCanvas>
  </div>
</template>

<script>
import DrawingCanvas from './components/DrawingCanvas.vue'

export default {
  name: 'App',
  components: {
    DrawingCanvas
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
