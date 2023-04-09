<template>
  <MainPage/>
</template>

<script>
import MainPage from './components/MainPage.vue'

export default {
  name: 'App',
  components: {
    MainPage
  }
}
</script>

<style>
@import './vendor/normalize.css';
@import './vendor/TenorSans.css';
#app {
  font-family: 'Tenor Sans', Avenir, Helvetica, Serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body {
  margin: 0;
  padding: 0;
  background-color: #000b24;
}
::-webkit-scrollbar {
  width: 0;
}
</style>
