<template>
  <div id="app">
    <Stopwatch />
  </div>
</template>

<script>
import Stopwatch from './components/Stopwatch.vue';

export default {
  name: 'App',
  components: {
    Stopwatch,
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
  background-color: #fff;
  border-radius: 10px;
}
</style>
