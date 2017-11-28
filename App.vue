<template>
  <div id="app">
    <ProjectsSlider/>
    <Login/>
    <Resources/>
  </div>
</template>

<script>
import Resources from "./components/Resources";
import Resource from "./components/Resource";
import Skills from "./components/Skills";
import Login from "./components/Login";
import ProjectsSlider from "./components/ProjectsSlider"

export default {
  name: "app",
  components: {
    Login,
    Resource,
    Resources,
    Skills,
    ProjectsSlider
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
