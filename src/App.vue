<template>
  <div id="app">
    <Shopee/>
  </div>
</template>

<script>
import Shopee from './components/Shopee'

export default {
  name: 'app',
  components: {
    Shopee
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;

}
</style>
