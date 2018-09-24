<template>
  <div id="app">
    <Dlocation/>
  </div>
</template>

<script>
import Dlocation from './components/Dlocation.vue'

export default {
  name: 'app',
  components: {
    Dlocation
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
}
  body{
    margin: 0px;


  }

</style>
