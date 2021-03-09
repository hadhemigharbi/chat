<template>   
<div class="app">
  <h1 class="text-3xl font-extrabold uppercase flex justify-center mt-6">Hello</h1>               
  <Appmain />
</div>
</template>

<script>
import Appmain from './components/Appmain';
export default {
  name: 'App',
  components: { Appmain },
  
}
</script>

<style lang="scss">
h1 {
  color: #Fe2336;
}
</style>
