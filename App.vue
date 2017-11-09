<template>
  <div id="app">

    <Resources/>
    <Skills/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Resources from './components/Resources'
import Skills from './components/Skills'

export default {
  name: 'app',
  components: {
    Resources,
    Skills
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
