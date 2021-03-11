<template>   
<div class="app">              
  <UI />
</div>
</template>

<script>
import Appmain from './components/UI';
export default {
  name: 'App',
  components: { UI },
  
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
