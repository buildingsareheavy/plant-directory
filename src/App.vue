<template>
  <div id="app">
    <API/>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import API from "./components/Api.vue";
export default {
  name: "app",
  components: {
    HelloWorld,
    API
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
