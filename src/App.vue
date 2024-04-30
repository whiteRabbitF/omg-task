<template>
  <div id="app">
    <VerticalList />
  </div>
</template>

<script>
import VerticalList from './components/VerticalList.vue';

export default {
  components: {
    VerticalList,
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
