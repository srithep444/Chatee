<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'App'

}
</script>

<style>
html {
  height: 100%;
}
body {
  display: flex;
  justify-content: center;
  height: 100%;
  background: url('./assets/img1.jpg') 0 0 no-repeat;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
