<template>
  <canvas
    ref="xaxis"
    :width="this.canvasWidth"
    :height="this.canvasHeight"
    class="xaxis"
  ></canvas>
</template>

<script>
export default {
  name: 'XAxis',

  data() {
    return {
      ctx: null,
    };
  },

  props: {
    timeData: {
      type: Array,
      required: true,
    },

    unitWidth: {
      type: Number,
      required: true,
    },

    startIndex: {
      type: Number,
      required: true,
    },

    graphBoxMargin: {
      type: Number,
      required: true,
    },

    canvasWidth: {
      type: Number,
      required: true,
    },

    canvasHeight: {
      type: Number,
      default: 50,
    },
  },

  methods: {
    writeXAxis() {
      this.timeData.forEach(([time, index]) => {
        this.ctx.fillText(
          `${time}`,
          this.graphBoxMargin +
            this.unitWidth * (index - this.startIndex) -
            this.ctx.measureText(`${time}`).width / 2,
          20
        );
      });
    },
  },

  mounted() {
    this.ctx = this.$refs.xaxis.getContext('2d');
  },

  watch: {
    timeData() {
      this.ctx.clearRect(0, 0, this.canvasWidth, this.canvasHeight);
      this.writeXAxis();
    },
  },
};
</script>

<style>
.x-axis {
}
</style>
