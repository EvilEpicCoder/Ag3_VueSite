<template>
  <div id="app">
    <myHeader></myHeader>
    <myMenu></myMenu>
    <myContent></myContent>
    <myFooter></myFooter>
    <!-- router-view/ -->
  </div>
</template>

<script>
import myHeader from './components/Header'
import myMenu from './components/Menu'
import myContent from './components/Content'
import myFooter from './components/Footer'

export default {
  name: 'app',
  components: {
    myHeader,
    myMenu,
    myContent,
    myFooter
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
