<template>
  <NavBar></NavBar>
  <router-view/>
</template>
<script>
import NavBar from './components/NavBar'
export default {
  components: { NavBar },
  
}
</script>
<style>
body {
  background: linear-gradient(to left, #d714ca,#756be2);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 1000px;
  margin: 10px auto;
  color: #2c3e50;
}
</style>
