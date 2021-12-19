<template>
  <div id="app">
    <nav-bar/>
    <empleados/>
  </div>
</template>

<script>

import NavBar from './components/NavBar.vue'
import Empleados from './components/Empleado.vue'
export default {
  name: 'App',
  components: {
   NavBar,Empleados
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
</style>
