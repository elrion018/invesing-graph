<template>
  <div class="chart-menu" :style="style">
    <button
      class="chart-menu-button"
      @click="$emit('handle-chart-menu-button-click', $event)"
      value="1D"
    >
      1D
    </button>
    <button
      class="chart-menu-button"
      @click="$emit('handle-chart-menu-button-click', $event)"
      value="1W"
    >
      1W
    </button>
    <button
      class="chart-menu-button"
      @click="$emit('handle-chart-menu-button-click', $event)"
      value="1M"
    >
      1M
    </button>
    <button
      class="chart-menu-button"
      @click="$emit('handle-chart-menu-button-click', $event)"
      value="1Y"
    >
      1Y
    </button>
    <button
      v-if="isCandle"
      class="chart-menu-button"
      @click="$emit('handle-chart-menu-button-click', $event)"
      value="Linear"
    >
      Linear
    </button>
    <button
      v-if="!isCandle"
      class="chart-menu-button"
      @click="$emit('handle-chart-menu-button-click', $event)"
      value="Candle"
    >
      Candle
    </button>
  </div>
</template>

<script>
export default {
  name: 'ChartMenu',
  props: {
    canvasWidth: {
      type: Number,
      required: true,
    },

    canvasHeight: {
      type: Number,
      default: 20,
    },

    isCandle: {
      type: Boolean,
      required: true,
    },
  },

  computed: {
    style() {
      return {
        height: this.canvasHeight + 'px',
      };
    },
  },
};
</script>

<style>
.chart-menu {
  display: flex;
}

.chart-menu-button {
  flex: 1;
}
</style>
