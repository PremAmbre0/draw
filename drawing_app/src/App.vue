<template>
  <div id="app">
    <DrawingCanvas class="drawing-canvas"></DrawingCanvas>
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
  margin-top: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
