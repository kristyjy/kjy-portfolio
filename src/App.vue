<template>
  <main id="app">
    <Masthead />
    <Skills />
    <CodepenExamples />
  </main>
</template>

<script>
import '../node_modules/normalize.css/normalize.css';
import './css/variables.css';
import Masthead from './components/Masthead.vue';
import Skills from './components/Skills.vue';
import CodepenExamples from './components/CodepenExamples.vue';

export default {
  name: 'app',
  components: {
    Masthead,
    Skills,
    CodepenExamples
  }
}
</script>

<style>
*,
*:before,
*:after {
  box-sizing: border-box;
}

html {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-family: var(--font-primary), sans-serif;
  font-size: 62.5%;
  color: #333;
}

html,
body {
  width: 100%;
  height: 100%;
}

body {
  font-size: 16px;
}

h1,
h2,
h3,
h4 {
  font-family: var(--font-heading), cursive;
  font-weight: normal;
  text-align: center;
}
</style>
