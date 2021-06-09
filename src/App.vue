<template>
  <div id="app">
    <chart :canvasWidth="300" :canvasHeight="300"></chart>
  </div>
</template>

<script>
import Chart from './components/Chart.vue';

export default {
  name: 'App',
  components: {
    Chart,
  },
};
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
