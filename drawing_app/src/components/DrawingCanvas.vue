<template>
  <div class="canvas">
    <canvas ref="canvas" 
    :width="width"
    :height="height">
    </canvas>
  </div>
</template>

<script>
export default {
  name: 'DrawingCanvas',
  data() {
    return {
      hieght:0,
      width:0,
    }
  },
  computed: {
    canvas: function () {
      return this.$refs.canvas;
    },
    ctx: function () {
      return this.canvas.getContext('2d');
    }
  },
  mounted() {
    window.addEventListener('resize',this.handleResize);
    this.handleResize();
    this.draw();
  },
  methods: {
  handleResize: function(){
    console.log('resized');
    this.height = (window.innerHeight/100)*90  ;
    this.width = (window.innerWidth/100)*50 ;
    },
  draw: function(){
    let c = this.ctx
    c.strokeStyle = "red";
    c.strokeRect(0, 0, 100, 100);
  },
  },
}
</script>

<style>
.canvas {
  border: 1px solid #000;
}
</style>