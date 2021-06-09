<template>
  <canvas
    ref="yaxis"
    :width="this.canvasWidth"
    :height="this.canvasHeight"
  ></canvas>
</template>

<script>
export default {
  name: 'YAxis',

  props: {
    valueData: {
      type: Array,
      required: true,
    },

    graphBoxHeight: {
      type: Number,
      required: true,
    },

    canvasHeight: {
      type: Number,
      required: true,
    },

    canvasWidth: {
      type: Number,
      default: 50,
    },

    floorValue: {
      type: Number,
      required: true,
    },

    graphBoxMargin: {
      type: Number,
      required: true,
    },

    currentValue: {
      type: Number,
      required: true,
    },

    currentHeight: {
      type: Number,
      required: true,
    },
  },

  data() {
    return {
      ctx: null,
    };
  },

  methods: {
    writeYAxis() {
      for (let i = 0; i < this.valueData.length; i++) {
        let value = this.valueData[i];
        this.ctx.fillText(
          `${(this.floorValue + value).toFixed(3)}`,
          0,
          this.graphBoxMargin +
            (this.graphBoxHeight / this.valueData.length) * i +
            4
        );
      }
    },

    writeCurrent() {
      this.ctx.fillStyle = 'red';
      this.ctx.fillText(
        `${this.currentValue.toFixed(3)}`,
        0,
        this.currentHeight
      );
      this.ctx.fillStyle = 'black';
    },
  },

  mounted() {
    this.ctx = this.$refs.yaxis.getContext('2d');
  },

  watch: {
    valueData() {
      this.ctx.clearRect(0, 0, this.canvasWidth, this.canvasHeight);
      this.writeYAxis();
      this.writeCurrent();
    },
  },
};
</script>

<style></style>
