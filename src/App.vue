<template>
  <div id="app">
    <div v-for="item in [1,2,3,4,5,6,7,7,8]" v-bind:key="item">
      <Cell />
    </div>
  </div>
</template>

<script>
import Cell from "./components/Cell.vue";

export default {
  name: "app",
  components: {
    Cell
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
