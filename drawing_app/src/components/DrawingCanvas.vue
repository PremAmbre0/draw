<template>
  <div class="canvas-container">
    <canvas ref="canvas" class="canvas" height="600" width="800"></canvas>
    <div class="controls">
    <div class="brush">
      <div class="brush-thicknes">
        <button class="btn" @click="increment">+</button>
        <div class="brush-thicknes--value">{{thickness}}</div>
        <button class="btn" @click="decrement">-</button>
      </div>
      <div class="colorpicker">
        <label for="colorpicker"><input type="color" ref="colorpicker" name="colorpicker" @input="changeColor"></label>
      </div>
    </div>
    <div class="close">
      <button @click="clearCanvas" class="btn">X</button>
    </div>
    </div>
  </div>
</template>

<script>
import { fabric } from "fabric";

export default {

  data() {
    return {
      thickness:10,
      color:'#000'
    }
  },
  watch:{
    thickness(){
      this.manipulator(this.canvas,this.color, this.thickness)
    },
    color(){
      this.manipulator(this.canvas,this.color, this.thickness)
    }
  },
  computed:{
    canvas() {
      const ref = this.$refs.canvas;
      const canvas  = new fabric.Canvas(ref);
      return canvas
    }
  },
  mounted() {
    this.canvas.isDrawingMode = true;
    this.manipulator(this.canvas,this.color, this.thickness)
  },
  methods: {
    manipulator : function(canvas,color, thickness){
      canvas.freeDrawingBrush.color = color;  
      canvas.freeDrawingBrush.width = parseInt(thickness)
    },
    increment: function(){
      if(this.thickness==100){
        return
      }
      this.thickness +=5;
    },
    decrement: function(){
      if(this.thickness==0){
        return
      }
      this.thickness -=5;
    },
    changeColor: function(){
      const color = this.$refs.colorpicker.value;
      this.color = color;
    },
    clearCanvas : function (){
      this.canvas.clear(); 
    }
  },
};
</script>

<style lang="scss">
.canvas {
  border: 1px solid #000;
  background-color: #fff;

}
.canvas-container{
  height:65rem;
  width:80rem;
  background-color: $steel-blue;
}
</style>