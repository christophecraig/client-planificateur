<template>
  <div id="app">
    <Projects/>
    <Login/>
    <!-- <Resources> -->
        <Resource/>
    <!-- </Resources> -->
    <Skills/>
  </div>
</template>

<script>
import Resources from "./components/Resources";
import Resource from "./components/Resource";
import Skills from "./components/Skills";
import Login from "./components/Login";
import Projects from "./components/Projects"

export default {
  name: "app",
  components: {
    Login,
    Resource,
    Resources,
    Skills,
    Projects
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
