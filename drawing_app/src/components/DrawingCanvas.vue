<template>
  <div class="canvas-container">
    <canvas ref="canvas" class="canvas" height="600" width="800"></canvas>
    <div class="controls">
      <div class="brush">
        <div class="brush-thickness">
          <button class=" brush-thicknss--increment btn" @click="increment">+</button>
          <div class="brush-thickness--value">{{ thickness }}</div>
          <button class="brush-tickness--decrement btn" @click="decrement">-</button>
        </div>
        <div class=" brush-colorpicker-container">
          <label for="colorpicker"><input type="color" class="brush-colorpicker-input" ref="colorpicker"
              name="colorpicker" @input="changeColor"></label>
        </div>
        <div class="close">
          <button @click="clearCanvas" class=" btn">X</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { fabric } from "fabric";

export default {

  data() {
    return {
      thickness:"10",
      color: '#000',
      canvas: null
    }
  },
  watch: {
    thickness() {
      this.manipulator(this.canvas, this.color, this.thickness)
    },
    color() {
      this.manipulator(this.canvas, this.color, this.thickness)
    }
  },
  mounted() {
    this.canvas = new fabric.Canvas(this.$refs.canvas);
    this.canvas.isDrawingMode = true;
    this.manipulator(this.canvas, this.color, this.thickness)
  },
  methods: {
    manipulator: function (canvas, color, thickness) {
      canvas.freeDrawingBrush.color = color;
      canvas.freeDrawingBrush.width = thickness
    },
    changeColor: function () {
      const color = this.$refs.colorpicker.value;
      this.color = color;
    },
    clearCanvas: function () {
      this.canvas.clear();
    }
  },
};
</script>

<style lang="scss">
.canvas {
  border: 1px solid #000;
  // background-color: #fff;

}

.canvas-container {
  height: 65rem;
  width: 80.2rem;
  position: relative;
}

.brush {
  margin-top: 0.1rem;
  height: 5rem;
  width: 100%;
  background-color: $steel-blue;

  &-thickness {
    position: absolute;
    bottom: 1rem;
    display: flex;
    align-items: center;
    justify-content: space-around;

    &--value {
      background-color: #fff;
      height: 3rem;
      width: 3rem;
      font-size: 2rem;
      text-align: center;
      line-height: 3rem;
    }
  }

  &-colorpicker {
    &-container {
      position: absolute;
      bottom: 1rem;
      left: 11rem;
    }

    &-input {
      height: 3rem;
      width: 3rem;
      margin: 0 2rem 0 2rem
    }
  }
}

.close {
  position: absolute;
  bottom: 1rem;
  right: 1rem;

}

.btn {
  height: 3rem;
  width: 3rem;
  margin: 0 1rem 0 1rem
}
</style>