<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="GG Lah guys" /> -->
    <search-music></search-music>
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import SearchMusic from "./components/SearchMusic.vue";

export default {
  name: "App",
  components: {
    // HelloWorld,
    SearchMusic,
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
