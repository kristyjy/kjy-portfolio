<template>
  <div id="app">
    <Masthead />
  </div>
</template>

<script>
import '../node_modules/normalize.css/normalize.css';
import Masthead from './components/Masthead.vue'

export default {
  name: 'app',
  components: {
    Masthead
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
