<template>
  <div>
    <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
    <SortingVisualizer></SortingVisualizer>
  </div>
</template>

<script>
import SortingVisualizer from "./components/SortingVisualizer";
export default {
  name: "App",
  components: {
    SortingVisualizer
  }
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
